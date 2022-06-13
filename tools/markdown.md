# 格式

&emsp;&emsp;测试文本空格  
~~删除线~~
>最外层
>>第一层
>>>第二层

:注释  
使用 <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd> 重启电脑

# 希腊字母

$$
\alpha \quad  \beta \quad \gamma  \quad \Gamma \quad \delta \quad \Delta \quad \epsilon \quad \varepsilon \quad \zeta \quad \theta \quad \eta \quad  \vartheta  \quad \pi \quad  \phi \quad  \psi  \quad \omega \quad  \sigma \quad  \Sigma \quad  \nu  \quad \xi  \quad \lambda  \quad \Lambda \mu \quad  \partial \quad  \lbrace \quad  \rbrace $$

```
\alpha \beta \gamma \Gamma \delta \Delta \epsilon \varepsilon \zeta \theta \eta \vartheta \pi \phi \psi \omega \sigma \Sigma \nu \xi \lambda 
\Lambda \mu \partial \lbrace \rbrace
```

# 矩阵
$$
\begin{matrix}
1 & 2& 3\\
1 & 2& 3\\
1 & 2& 3\\
\end{matrix}\tag{1}
$$

$$
\begin{vmatrix}
1 & 2& 3\\
1 & 2& 3\\
1 & 2& 3\\
\end{vmatrix}
\tag{1}
$$
$$
\begin{Vmatrix}
1 & 2& 3\\
1 & 2& 3\\
1 & 2& 3\\
\end{Vmatrix}
\tag{1}
$$


$$
\begin{bmatrix}
1 & 2& 3\\
1 & 2& 3\\
1 & 2& 3\\
\end{bmatrix}
\tag{1}
$$

$$
\begin{Bmatrix}
1 & 2& 3\\
1 & 2& 3\\
1 & 2& 3\\
\end{Bmatrix}\tag{1}
$$


$$
\begin{Bmatrix}
1 & 2&\cdots& 3\\
1 & 2&\cdots& 3\\
\vdots &\vdots &\ddots& 3\\
1 & 2&\cdots& 3\\
\end{Bmatrix}\tag{1}
$$

$$
\left[
\begin{array}{cc|c}
1 & 2& 3\\
1 & 2& 3
\end{array}
\right]
$$

$$
P(x|a_x)=\begin{cases}
1, & x=f(a_x) \\
0, & other\ values
\end{cases}
$$


# 数学公式
|符号|实现|符号|实现|
|----|----|----|----|
|$\sum$|\sum|$\sum_{i=0}^n$|\sum_{i=0}^n|
|$\times$|\times|$\pm$|\pm|
|$\div$|\div|$\mid$|\mid|
|$\cdot$|\cdot|$\circ$|\circ|
|$\ast$|\ast|$\le$|\le|
|$\ge$|\ge|$\approx$|\approx|
|$\prod$|\prod|$\cdots$|\cdots|
|$\int$|\int|$\infty$|\infty|
|$\therefore$|\therefore|$\forall$|\forall|
|$\exist$|\exist|$\subset$|\subset|
|$\subseteq$|\subseteq|$\bigcup$|\bigcup|
|$\bigcap$|\bigcap|$\bigvee$|\bigvee|
|$\bigwedge$|\bigwedge|$\hat{y}$|\hat{y}|
|$\hat{y}$|\hat{y}|$\dot{y}$|\dot{y}|
|$\widetilde{y}$|\widetilde{y}|$\ddot{y}$|\ddot{y}|
|$\overline{a+b+c+d}$|\overline{a+b+c+d}|$\underline{a+b+c+d}$|\underline{a+b+c+d}|
|$\overbrace{a+\underbrace{b+c}_{1.0}+d}^{2.0}$|\overbrace{a+\underbrace{bc}_{1.0}+d}^{2.0}|$\uparrow$|\uparrow|
|$\Uparrow$|\Uparrow|$\downarrow$|\downarrow|
|$\Downarrow$|\Downarrow|$\leftarrow$|\leftarrow|
|$\Leftarrow$|\Leftarrow|$\rightarrow$|\rightarrow|
|$\Rightarrow$|\Rightarrow|
|$\frac{a}{b}$|\frac|


# 制图
```mermaid
pie
    title 为什么总是宅在家里？
    "喜欢宅" : 15
    "天气太热或太冷" : 20
    "穷" : 500
```


```mermaid
graph LR
emperor((朱八八))-.子.->朱五四-.子.->朱四九-.子.->朱百六


朱雄英--长子-->朱标--长子-->emperor
emperor2((朱允炆))--次子-->朱标
朱樉--次子-->emperor
朱棡--三子-->emperor
emperor3((朱棣))--四子-->emperor
emperor4((朱高炽))--长子-->emperor3
```

```mermaid
graph LR
A[方形] -->B(圆角)
    B --> C{条件a}
    C -->|a=1| D[结果1]
    C -->|a=2| E[结果2]
```

```mermaid
graph TB %% comments
  %% Entity[Text]
  ID-1[Node 1]
  ID-2>Node 2]
  ID-3(Node 3 <br> text)
  %% Entity--Entity
  ID-1---ID-2
  ID-1 --> ID-3
  %% Entity--Text--Entity
  ID-2--Link between 2 and 3---ID-3
  ID-3-->|Action from 3 to 1|ID-1
  ID-3 -- "Action from 3 to 2. p/w: '_-!#$%^&*+=?,\'" --> ID-2
  %% Complex cases
  A[Hard edge] -->|Link text| B(Round edge)
  ID-1---ID-2(Text)
  B --> C{Text}
  C -->|One| D[Text]
  A(A) --> B(B)
  C[/C/] --> D>D]
  %% class/classDef
  classDef blue fill:#08f,stroke:#fff;
  class ID-1 blue
  class ID-1,ID-2 red
  %% click
  click ID-1 "https://github.com" "Tooltip text" %% comments
  click ID-2 alert "Tooltip for a callback"
  %% subgraph
  subgraph A subgraph
    ID-4{Node 4}
    ID-5((fa:fa-spinner))
    ID-6["Node 6 (same #quot;shape#quot;)"]
    ID-4-.->ID-5
    ID-5 -. Action from 5 to 4 .-> ID-4
    ID-5==>ID-6
    ID-6 == Action from 6 to 5 ==> ID-5
  end
```

```mermaid
sequenceDiagram %% diagram
  autonumber
  %% participant
  participant Alice
  participant B as Bob<br>Newline
  participant C as Carol
  %% arrows
  B->C: Solid line without arrow
  B-->C: Dotted line without arrow
  B->>C:Solid line with arrowhead
  B-->>C: Dotted line with arrowhead
  B-)C: Solid line with Async arrow
  B--)C: Dotted line with Async arrow
  B-xC: Solid line with a cross at end
  B--xC: Dotted line with a cross at end
  %% activation, shorthand
  activate Alice
  B->>+C: Arrow with + that activates Carol
  C->>-B: Arrow with - that deactivates Carol
  deactivate Alice
  %% notes
  Note left of Alice: Alice likes to chat
  Note over B,C: Bob whispers when sick
  %% loop
  loop Every minute
    B-->C: Can you hear me?
  end
  %% alt
  alt is sick
    B-->C: Not so good :(
  else is well
    B->C: Feeling fresh like a daisy
  end
  opt Extra response
    B->C: You, Carol?
  end
  %% par
  par Action 1
    B-->C: I'm good
  and Action 2
    B->>C: I'm better now
  end
  rect rgba(128, 128, 128, 0.5)
    B->>C: So colourful!
  end
```

```mermaid
gantt %%comment
  dateFormat  YYYY-MM-DD
  axisFormat  %m/%d/%Y
  title Adding GANTT diagram functionality to mermaid
  section A section %%comment
  Completed task            :done,    des1, 2014-01-06,2014-01-08
  Active task               :active,  des2, 2014-01-09, 3d
  Future task               :         des3, after des2, 5d %%comment
  Future task2               :         des4, after des3, 5d
  A task           :a1, 2014-01-01, 30d
  section Critical tasks
  Completed task in the critical line :crit, done, 2014-01-06,24h
  Implement parser and jison          :crit, done, after des1, 2d
  Create tests for parser             :crit, active, 3d
  Future task in critical line        :crit, 5d
  Create tests for renderer           :2d
  Add to mermaid                      :1d
```


```mermaid
classDiagram
  Animal <|-- Duck : LabelText
  class1 --o other
  Animal --o Fish
  Animal : +int age
  Animal : +String gender
  Animal: mate()
  Animal : #method(param)* return
  class Duck{
      %% Class Members
      +String beakColor
      #quack()
  }
  class Fish{
      -abstractMethod()*
      staticMethod()$
  }
  %% Class member generics
  class Square~Shape~{
      List~int~ position
      setPoints(List~int~ points)
      getPoints() List~int~
  }
  Square : -List~string~ messages
  Square : ~setMessages(List~string~ messages)
  Square : +getMessages() List~string~

  %% Multiplicity relations
  Customer "1" --> "*" Ticket
  Student "1" --> "1..*" Course
  Galaxy --> "6" Star : Contains

  %% Annotations
  class Annotate1
  <<interface>> Animal

  class Annotate2{
    <<Service>>
  }

```


```mermaid
stateDiagram %%comment
  s1
  state "Description with parenthesis" as s2
  s3 : Description with colon

  s1 --> s2
  s2 --> s3: Colon transition
  [*] --> s1 : Transition text
  s3 --> [*]

  state NestedComposite {
      [*] --> Nested

      state Nested {
          [*] --> second
      }
  }
```


```mermaid
journey
    title My working day
    section Go to work
      Make tea: 5: Me
      Go upstairs: 3: Me
      Do work: 1: Me, Cat
    section Go home
      Go downstairs: 5: Me
      Sit down: 5: Me
```



