# Markdown使用笔记

## 用例 按钮

+ 示例

  + [code]

    ```markdown
    01: <kbd>Ctrl</kbd>
    ```

  + [demo]

    <kbd>Ctrl</kbd>

## 用例 链接

+ 示例

  + [code]

    ```markdown
    01: [(CSDN)Markdown 状态图绘制详解](https://blog.csdn.net/u014696856/article/details/135652884)
    ```

  + [demo]

    [(CSDN)Markdown 状态图绘制详解](https://blog.csdn.net/u014696856/article/details/135652884)

## 用例 图片

+ 示例

  + [code]

    ```markdown
    01: ![Turing Example 01](./images2/TuringMachine-Example26052901a.svg)  
    02: ![Data Structure Turing Example 1](./images/Python-DataStructure-260529a1.png)
    ```

  + [demo]  
    ![Turing Example 01](./images2/TuringMachine-Example26052901a.svg)  

  + [demo]  
    ![Data Structure Turing Example 1](./images/Python-DataStructure-260529a1.png)  

## 用例 表格

+ 示例

  + [code]

    ```markdown
    01: | current_status | reading_sign   | new_sign    | new_status | move_directory |
    02: | :------------: | :------------: | :---------: | :--------: | :------------- |
    03: | Data.State     |                | Data.Symbol |            |                |
    04: | --             | -              | -           | --         | -              |
    05: | S0             | a              | B           | S1         | R              |
    06: | S1             | a              | a           | S1         | R              |
    07: | S1             | b              | b           | S1         | R              |
    08: | S1             | B              | B           | S2         | L              |
    09: | S2             | b              | B           | S3         | L              |
    10: | S3             | b              | b           | S3         | L              |
    11: | S3             | a              | a           | S3         | L              |
    12: | S3             | B              | B           | S0         | R              |
    13: | S0             | B              | B           | SY         | N              |
    14: | S0             | b              | b           | SN         | R              |
    15: | S2             | a              | a           | SN         | R              |
    16: | S2             | B              | B           | SM         | R              |
    ```

  + [table]

    | current_status | reading_sign   | new_sign    | new_status | move_directory |
    | :------------: | :------------: | :---------: | :--------: | :------------- |
    | Data.State     |                | Data.Symbol |            |                |
    | --             | -              | -           | --         | -              |
    | S0             | a              | B           | S1         | R              |
    | S1             | a              | a           | S1         | R              |
    | S1             | b              | b           | S1         | R              |
    | S1             | B              | B           | S2         | L              |
    | S2             | b              | B           | S3         | L              |
    | S3             | b              | b           | S3         | L              |
    | S3             | a              | a           | S3         | L              |
    | S3             | B              | B           | S0         | R              |
    | S0             | B              | B           | SY         | N              |
    | S0             | b              | b           | SN         | R              |
    | S2             | a              | a           | SN         | R              |
    | S2             | B              | B           | SM         | R              |

## 用例 LaTeX

### "LaTeX"概述

#### 基本语法结构

+ 命令, 以 `\` 开始，
  + 如 `\alpha` $\alpha$

+ 参数, 以 `{}` 包围
  + 如 `\frac{a}{b}` $\frac{a}{b}$

+ 下标, 以 `_` 标注
  + 如， `X_2` $X_2$

+ 上标, 以 `^` 标注
  + 如， `X^2` $X^2$

+ `$`行 vs `$$`块

#### 希腊字符

| code       | demo       | note  | code       | demo       | note  |
| :--------  | :--------- | :---- | :--------  | :--------- | :---- |
| `\alpha`   | $\alpha$   |       | `\Alpha`   | $\Alpha$   |  A    |
| `\beta`    | $\beta$    |       | `\Beta`    | $\Beta$    |  B    |
| `\delta`   | $\delta$   |       | `\Delta`   | $\Delta$   |       |
| `\epsilon` | $\epsilon$ |       | `\Epsilon` | $\Epsilon$ |  E    |
| `\gamma`   | $\gamma$   |       | `\Gamma`   | $\Gamma$   |       |
| `\lambda`  | $\lambda$  |       | `\Lambda`  | $\Lambda$  |       |
| `\mu`      | $\mu$      |       | `\Mu`      | $\Mu$      |  M    |
| `\nu`      | $\nu$      |       | `\Nu`      | $\Nu$      |  N    |
| `\omega`   | $\omega$   |       | `\Omega`   | $\Omega$   |       |
| `\phi`     | $\phi$     |       | `\Phi`     | $\Phi$     |       |
| `\pi`      | $\pi$      |       | `\Pi`      | $\Pi$      |       |
| `\rho`     | $\rho$     |       | `\Rho`     | $\Rho$     |  P    |
| `\sigma`   | $\sigma$   |       | `\Sigma`   | $\Sigma$   |       |
| `\tau`     | $\tau$     |       | `\Tau`     | $\Tau$     |  T    |
| `\theta`   | $\theta$   |       | `\Theta`   | $\Theta$   |       |

#### 算术符号

| code          | demo          | note  |
| :------------ | :------------ | :---- |
| `+`           | $+$           |       |
| `-`           | $-$           |       |
| `\times`      | $\times$      |       |
| `\div`        | $\div$        |       |
| `\frac{a}{b}` | $\frac{a}{b}$ |       |
| `\sqrt{a}`    | $\sqrt{a}$    |       |
| `\sqrt[n]{x}` | $\sqrt[n]{x}$ |       |
| `x^n`         | $x^n$         |       |
| `e^{i\pi}`    | $e^{i\pi}$    |       |

#### 条件符号

| code             | demo             | note  |
| :--------------- | :--------------- | :---- |
| `\wedge`         | $\wedge$         | and   |
| `\vee`           | $\vee$           | or    |
| `\neg`           | $\neg$           | not   |

#### 比较符号

| code             | demo             | note  |
| :--------------- | :--------------- | :---- |
| `=`              | $=$              |       |
| `\neq`           | $\neq$           |       |
| `\equiv`         | $\equiv$         |       |
| `<`              | $<$              |       |
| `>`              | $>$              |       |
| `\leq`           | $\leq$           |       |
| `\geq`           | $\geq$           |       |
| `\approx`        | $\approx$        |       |
| `\sim`           | $\sim$           |       |

#### 集合符号

| code             | demo             | note  |
| :--------------- | :--------------- | :---- |
| `\in`            | $\in$            |       |
| `\notin`         | $\notin$         |       |
| `\subset`        | $\subset$        |       |
| `\subseteq`      | $\subseteq$      |       |
| `\supset`        | $\supset$        |       |
| `\supseteq`      | $\supseteq$      |       |
| `\cap`           | $\cap$           |       |
| `\cup`           | $\cup$           |       |
| `\emptyset`      | $\emptyset$      |       |
| `\Join`          | $\Join$          |       |

#### 特殊函数和符号

| code             | demo             | note  |
| :--------------- | :--------------- | :---- |
| `\sin`           | $\sin$           |       |
| `\cos`           | $\cos$           |       |
| `\tan`           | $\tan$           |       |
| `\log_{a}{b}`    | $\log_{a}{b}$    |       |
| `\ln{a}`         | $\ln{a}$         |       |
| `\lim_{x \to 0}` | $\lim_{x \to 0}$ |       |
| `\sum_{i=1}^{n}` | $\sum_{i=1}^{n}$ |       |
| `\int_{a}^{b}`   | $\int_{a}^{b}$   |       |
| `\infty`         | $\infty$         |       |

#### 矩阵

+ [code]

  01: `$$`  
  02: `  \begin{pmatrix}`  
  03: `    a & b \\`  
  04: `    c & d \\`  
  05: `  \end{pmatrix}`  
  06: `$$`  

+ [demo]

  $$
    \begin{pmatrix}
      a & b \\
      c & d \\
    \end{pmatrix}
  $$

+ [code]

  01: `$$`  
  02: `  \begin{bmatrix}`  
  03: `    a & b & c\\`  
  04: `    c & d & e\\`  
  05: `    e & f & g\\`  
  06: `  \end{bmatrix}`  
  07: `$$`

+ [demo]

  $$
    \begin{bmatrix}
      a & b & c\\
      c & d & e\\
      e & f & g\\
    \end{bmatrix}
  $$

+ [code]

  01: `$$`  
  02: `  \begin{vmatrix}`  
  03: `    a & b & c\\`  
  04: `    c & d & e\\`  
  05: `  \end{vmatrix}`  
  06: `$$`  

+ [demo]

  $$
    \begin{vmatrix}
      a & b & c\\
      c & d & e\\
    \end{vmatrix}
  $$

### 块级公式

+ [code]

  01: `$ E = mc^2 $`  
  02: `$ \int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi} $`  

+ [demo]

  $ E = mc^2 $  
  $ \int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi} $  

### 多行公式

+ [code]

  01: `$$`  
  02: `  \begin{align}`  
  03: `    f(x) &= ax^2 + bx + c \\`  
  04: `    f'(x) &= 2ax + b \\`  
  05: `    f''(x) & = 2a`  
  06: `  \end{align}`  
  07: `$$`  

+ [demo]

  $$
    \begin{align}
      f(x) &= ax^2 + bx + c \\
      f'(x) &= 2ax + b \\
      f''(x) & = 2a
    \end{align}
  $$

## 用例 树

+ [code]

  01 `graph TD`  
  02 `    A[Root] --> B[Branch 1]`  
  03 `    A --> C[Branch 2]`  
  04 `    B --> D[Branch 3]`  
  05 `    B --> E[Leaf 2]`  
  06 `    C --> F[Leaf 3]`  
  07 `    D --> G[Branch 4]`  
  08 `    D --> H[left 4]`  

  Note: "graph TD" vs "graph LR"

+ [demo]

  ```mermaid
  graph TD

  A[Root] --> B[Branch 1]
  A --> C[Branch 2]
  B --> D[Branch 3]
  B --> E[Leaf 2]
  C --> F[Leaf 3]
  D --> G[Branch 4]
  D --> H[left 4]
  ```

+ [demo]

  ```mermaid
  graph LR
  
  A[Root] --> B[Branch 1]
  A --> C[Branch 2]
  B --> D[Branch 3]
  B --> E[Leaf 2]
  C --> F[Leaf 3]
  D --> G[Branch 4]
  D --> H[left 4]
  ```


## 用例 状态流转图

+ 参考
  [(CSDN)Markdown 状态图绘制详解](https://blog.csdn.net/u014696856/article/details/135652884)

+ 示例

  + [code]

    ```markdown
    01: ```mermaid
    02: stateDiagram
    03: begin --> state1:proc1
    04: ```
    ```

  + [demo]

    ```mermaid
    stateDiagram
    begin --> state1:proc1
    ```

+ 示例

  + [code]

    ```markdown
    01:   ```mermaid 
    02:   stateDiagram-v2
    03:       [*] --> 待支付
    04:       待支付 --> 已支付:支付成功
    05:       已支付 --> [*]
    06:   ```
    ```

  + [demo]

    ```mermaid
    stateDiagram-v2
    [*] --> 待支付
    待支付 --> 已支付:支付成功
    已支付 --> [*]
    ```

+ 示例，单嵌套

  + [code]

    ```markdown
    01:   ```mermaid
    02:   stateDiagram-v2
    03: 
    04:       [*] --> pNode
    05:       state pNode {
    06:           [*] --> cNode
    07:           cNode --> [*]
    08:       }
    09:   ```
    ```

  + [demo]

    ```mermaid
    stateDiagram-v2

        [*] --> pNode
            state pNode {
                [*] --> cNode
                cNode --> [*]
            }
    ```

+ 示例，多层嵌套

  + [code]

    ```markdown
    01:  ```mermaid
    02:  stateDiagram-v2
    03: 
    04:      [*] --> l1_Node
    05:      state l1_Node {
    06:          [*] --> l2_Node
    07:          state l2_Node {
    08:              [*] --> l3_Node
    09:              state l3_Node {
    10:                  [*] --> l4_Node
    11:                  state l4_Node {
    12:                      [*] --> core_Node
    13:                      core_Node --> [*]
    14:                  }
    15:              }
    16:          }
    17:      }
    18:  ```
    ```

  + [demo]

    ```mermaid
    stateDiagram-v2

        [*] --> l1_Node
        state l1_Node {
            [*] --> l2_Node
            state l2_Node {
                [*] --> l3_Node
                state l3_Node {
                    [*] --> l4_Node
                    state l4_Node {
                        [*] --> core_Node
                        core_Node --> [*]
                    }
                }
            }
        }
    ```
