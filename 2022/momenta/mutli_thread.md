## thread
```
std::set<int> int_set;
auto f = [&int_set]() {
    try {
        std::random_device rd;
        std::mt19937 gen(rd());
        std::uniform_int_distribution<> dis(1, 1000);
        for(std::size_t i = 0; i != 100000; ++i) {
            int_set.insert(dis(gen));
        }
    } catch(...) {}
};
std::thread td1(f), td2(f);
td1.join();
td2.join();
```
使用互斥对象std::mutex完成读写保护

|类名|描述含义|
|----|----|
|std::mutex|最简单互斥对象|
|std::timed_mutex|带有超时机制的互斥对象|
|std::recursive_mutex|允许一个线程内递归的Lock和Unlock|
|std::recursive_timed_mutex|递归超时对象|
使用互斥对象的Lock函数实现线程互斥
```
std::set<int> int_set;
std::mutex mt;
auto f = [&int_set, &mt]() {
    try {
        std::random_device rd;
        std::mt19937 gen(rd());
        std::uniform_int_distribution<> dis(1, 1000);
        for(std::size_t i = 0; i != 100000; ++i) {
            mt.lock();
            int_set.insert(dis(gen));
            mt.unlock();
        }
    } catch(...) {}
};
std::thread td1(f), td2(f);
td1.join();
td2.join();
```
模板类实现互斥
|模板类|描述含义|
|----|----|
|std::lock_guard|基于作用域及生命周期实现自动加锁与释放锁|
|std::unique_guard|基于作用域及生命周期实现自动加锁与释放锁，单可以通过手动操作实现锁生命周期的管理，比lock_guard占用空间稍大，效率稍低|
|std::shared_guard|用于管理可转移和共享所有权的互斥对象|

```
std::set<int> int_set;
std::mutex mt;
auto f = [&int_set, &mt]() {
    try {
        std::random_device rd;
        std::mt19937 gen(rd());
        std::uniform_int_distribution<> dis(1, 1000);
        for(std::size_t i = 0; i != 100000; ++i) {
            std::lock_guard<std::mutex> lck(mt);
            int_set.insert(dis(gen));
        }
    } catch(...) {}
};
std::thread td1(f), td2(f);
td1.join();
td2.join();
```

## condition_variable


```
#include <iostream>           // std::cout
#include <thread>             // std::thread
#include <mutex>              // std::mutex, std::unique_lock
#include <condition_variable> // std::condition_variable

std::mutex mtx;
std::condition_variable produce,consume;

int cargo = 0;     // shared value by producers and consumers

void consumer () {
  std::unique_lock<std::mutex> lck(mtx);
  while (cargo==0) consume.wait(lck);
  std::cout << cargo << '\n';
  cargo=0;
  produce.notify_one();
}

void producer (int id) {
  std::unique_lock<std::mutex> lck(mtx);
  while (cargo!=0) produce.wait(lck);
  cargo = id;
  consume.notify_one();
}

int main ()
{
  std::thread consumers[10],producers[10];
  // spawn 10 consumers and 10 producers:
  for (int i=0; i<10; ++i) {
    consumers[i] = std::thread(consumer);
    producers[i] = std::thread(producer,i+1);
  }

  // join them back:
  for (int i=0; i<10; ++i) {
    producers[i].join();
    consumers[i].join();
  }

  return 0;
}
```