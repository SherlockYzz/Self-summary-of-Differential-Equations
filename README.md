# 微分方程自总结V3[知识点+例题+做题技巧]
## 一、基本概念
1. **微分方程**：含有自变量 $x$、未知函数 $y(x)$ 及其各阶导数的方程，一般形式：
   $$F(x,y,y',y'',\dots,y^{(n)})=0$$

2. **阶**：方程中导数的最高阶数。
   - 例：$y'+2xy=e^x$ 是一阶微分方程；$y''-3y'+2y=0$ 是二阶微分方程。

3. **解**：使微分方程成为恒等式的函数 $y=y(x)$。

4. **通解**：含有独立任意常数的个数与方程阶数相同的解。
   - 例：一阶方程 $y'=2x$ 的通解为 $y=x^2+C$（含1个独立常数）。

5. **特解**：不含任意常数，或通解中任意常数被确定后的解。
   - 例：满足初始条件 $y(0)=1$ 的特解为 $y=x^2+1$。

6. **初始条件**：确定通解中任意常数的条件。
   - $n$ 阶方程需要 $n$ 个初始条件：$y(x_0)=y_0,\ y'(x_0)=y_0',\ \dots,\ y^{(n-1)}(x_0)=y_0^{(n-1)}$。

7. **线性微分方程**：未知函数 $y$ 和它的各阶导数都是一次项，且系数都是 $x$ 的函数。
   - 标准形式：$y^{(n)}+a_1(x)y^{(n-1)}+\dots+a_n(x)y=f(x)$
   - 当 $f(x)\equiv0$ 时为齐次线性方程，否则为非齐次线性方程。

---

## 二、一阶微分方程

### 2.0 一阶微分方程 通用判别与解题优先级

解题时严格按以下顺序依次判断，匹配到第一个类型即用对应解法，不要跳步。

**1. 最高优先级：一阶线性方程**

- **判定标准**：先整理为以 $y$ 为因变量的标准形式 $\boldsymbol{y'+p(x)y=q(x)}$。
- 若无法整理，立即交换 $x$ 和 $y$ 的地位，把 $x$ 看作 $y$ 的函数，整理为 $\boldsymbol{\dfrac{dx}{dy}+P(y)x=Q(y)}$。
- 这种“正难则反”技巧在 $y$ 作为因变量不是线性时尤其有效，是高频易错点。
- **核心解法**：公式法/积分因子法/常数变易法（见 2.3）。

**2. 第二优先级：可分离变量方程**

- **判定标准**：能整理为 $\boldsymbol{\dfrac{dy}{dx}=f(x)\cdot g(y)}$，左右两边可完全分离为只含 $x$ 和只含 $y$ 的项。
- 快速识别：方程中若出现 $f(x)$ 与 $g(y)$ 相乘或相除的形式，大概率是可分离变量型。
- **核心解法**：分离变量后两边直接积分（见 2.1）。

**3. 第三优先级：全微分方程（恰当方程）**

- **判定标准**：方程已写成对称形式 $P(x,y)dx+Q(x,y)dy=0$，且满足 $\boldsymbol{\dfrac{\partial P}{\partial y}=\dfrac{\partial Q}{\partial x}}$。
- 若不满足，可尝试寻找积分因子 $\mu(x,y)$ 乘到方程两边使之成为全微分方程。
- **核心解法**：凑全微分或线积分求原函数（见 2.5）。

**4. 第四优先级：齐次方程**

- **判定标准**：能整理为 $\boldsymbol{\dfrac{dy}{dx}=g\!\left(\dfrac{y}{x}\right)}$，右端是 $\dfrac{y}{x}$ 的一元函数。
- 快速判断：将方程中每个 $y$ 换成 $tx$、每个 $x$ 换成 $ty$，若方程形式不变，则为齐次型。
- **核心解法**：令 $u=\dfrac{y}{x}$，化为可分离变量方程（见 2.2）。

**5. 最低优先级：伯努利方程**

- **判定标准**：形似一阶线性，但右边多出一个 $y$ 的幂次项，标准形式为 $\boldsymbol{y'+p(x)y=q(x)y^\alpha\ (\alpha\neq0,1)}$。
- 快速识别：若方程中 $y'$ 和 $y$ 都是一次，但等号另一边出现 $y^2$、$y^3$、$\sqrt{y}$ 等，即为伯努利型。
- **核心解法**：令 $z=y^{1-\alpha}$，化为一阶线性方程（见 2.4）。

> **补充说明**：若方程能写成 $P(x,y)dx+Q(x,y)dy=0$ 且又不是以上类型，应优先检验是否全微分方程或能否找到积分因子。

---

### 2.1 可分离变量的微分方程

- **识别特征**：能直接写成 $\displaystyle\frac{dy}{dx}=f(x)g(y)$ 或 $P(x)Q(y)dx+M(x)N(y)dy=0$。
- **解法步骤**：
  1. 分离变量：将含 $y$ 的因子除到左边，含 $x$ 的因子乘到右边，得 $\displaystyle\frac{dy}{g(y)}=f(x)dx$（要求 $g(y)\neq0$）。  
  2. 两边积分：$\displaystyle\int\frac{dy}{g(y)}=\int f(x)dx$。  
  3. 求出积分，得到隐式通解（能显化的尽量显化）。
- **典型例题**：解方程 $\displaystyle\frac{dy}{dx}=2xy$

  **解**：分离变量得 $\displaystyle\frac{dy}{y}=2x\,dx$

  两边积分：$\displaystyle\int\frac{dy}{y}=\int 2x\,dx$

  得 $\ln|y|=x^2+C_1$

  整理为显式通解：$y=Ce^{x^2}$（其中 $C=\pm e^{C_1}$，$C=0$ 时 $y=0$ 也是解，已包含在内）

- **解题技巧**：
  - 分离变量时若除以 $g(y)$，需检查 $g(y)=0$ 的解是否丢失（奇解）。题目未特别说明时，一般默认求通解即可。
  - 形如 $\displaystyle\frac{dy}{dx}=f(ax+by+c)$ 的方程，令 $u=ax+by+c$，则 $\displaystyle\frac{du}{dx}=a+b\frac{dy}{dx}$，代入后可分离变量。
  - 积分后若出现 $\ln$，尽量用对数性质合并常数，将结果写成显函数形式。

---

### 2.2 齐次方程

- **识别特征**：方程可化为 $\displaystyle\frac{dy}{dx}=g\!\left(\frac{y}{x}\right)$，即右端是以 $\frac{y}{x}$ 为整体变量的函数。
- **解法步骤**：
  1. 换元：令 $u=\dfrac{y}{x}$，则 $y=ux$，两边对 $x$ 求导得 $\displaystyle\frac{dy}{dx}=u+x\frac{du}{dx}$。  
  2. 代入原方程：$u+x\dfrac{du}{dx}=g(u)$，整理得 $\displaystyle\frac{du}{g(u)-u}=\frac{dx}{x}$（可分离变量）。  
  3. 分离变量并积分，求出 $u(x)$。  
  4. 代回 $u=\dfrac{y}{x}$，得到原方程的通解。
- **典型例题**：解方程 $\displaystyle\frac{dy}{dx}=\frac{y}{x}+\tan\frac{y}{x}$

  **解**：令 $u=\dfrac{y}{x}$，则 $\dfrac{dy}{dx}=u+x\dfrac{du}{dx}$

  代入得：$u+x\dfrac{du}{dx}=u+\tan u$

  化简：$x\dfrac{du}{dx}=\tan u$

  分离变量：$\cot u\,du=\dfrac{dx}{x}$

  积分：$\displaystyle\int\cot u\,du=\int\frac{dx}{x}$

  得 $\ln|\sin u|=\ln|x|+C_1$，即 $\sin u=Cx$

  代回 $u=\dfrac{y}{x}$，通解为：$\sin\dfrac{y}{x}=Cx$

- **解题技巧**：
  - 形如 $\displaystyle\frac{dy}{dx}=f\!\left(\frac{a_1x+b_1y+c_1}{a_2x+b_2y+c_2}\right)$ 的方程，若 $c_1,c_2$ 不全为零，可通过解线性方程组找到平移量 $h,k$，令 $x=X+h,\ y=Y+k$ 消去常数项，化为齐次型。
  - 换元后得到的积分有时较复杂，可尝试用分部积分或凑微分法简化。

---

### 2.3 一阶线性微分方程（3种解法）

**标准形式**

- 以 $y$ 为因变量：$\boldsymbol{y'+p(x)y=q(x)}$
- 以 $x$ 为因变量：$\boldsymbol{\dfrac{dx}{dy}+P(y)x=Q(y)}$
- 当 $q(x)\equiv0$（或 $Q(y)\equiv0$）时为齐次线性方程，否则为非齐次线性方程。

**解题技巧：交换因变量视角**

若给定的方程以 $y$ 为因变量不是线性，但以 $x$ 为因变量却是线性，则用 $\dfrac{dx}{dy}+P(y)x=Q(y)$ 公式求解，最后将 $x$ 与 $y$ 换回即可。

---

#### 方法一：积分因子法（本质方法）

**原理**：给方程两边乘以积分因子 $\mu(x)$，使左边成为全微分，直接积分求解。

**解法步骤**

1. 将方程整理为标准形式 $y'+p(x)y=q(x)$  
2. 计算积分因子：$\boldsymbol{\mu(x)=e^{\int p(x)dx}}$（积分常数取0）  
3. 两边同乘 $\mu(x)$，左边化为全微分：
   $$\frac{d}{dx}\bigl[\mu(x)\cdot y\bigr]=\mu(x)\cdot q(x)$$
4. 两边积分：$\displaystyle\mu(x)\cdot y=\int \mu(x)\cdot q(x)\,dx+C$  
5. 整理得通解：$\displaystyle y=\frac{1}{\mu(x)}\left(\int \mu(x)\cdot q(x)\,dx+C\right)$

**典型例题**

解方程 $y'-\dfrac{2}{x}y=x+2$

1. $p(x)=-\dfrac{2}{x}$，$q(x)=x+2$  
2. 积分因子：$\mu(x)=e^{\int -\frac{2}{x}dx}=e^{-2\ln|x|}=\dfrac{1}{x^2}$  
3. 两边乘 $\mu(x)$：
   $$\frac{1}{x^2}y'-\frac{2}{x^3}y=\frac{1}{x}+\frac{2}{x^2}$$
   左边化为：$\displaystyle\frac{d}{dx}\!\left(\frac{y}{x^2}\right)=\frac{1}{x}+\frac{2}{x^2}$  
4. 积分：
   $$\frac{y}{x^2}=\int\left(\frac{1}{x}+\frac{2}{x^2}\right)dx+C=\ln|x|-\frac{2}{x}+C$$
5. 通解：$y=Cx^2+x^2\ln|x|-2x$

---

#### 方法二：常数变易法（理解公式来源）

**原理**：先求齐次通解，再将常数 $C$ 变易为函数 $C(x)$，代入非齐次方程确定 $C(x)$。

**解法步骤**

1. 求齐次方程 $y'+p(x)y=0$ 的通解：$\displaystyle y=Ce^{-\int p(x)dx}$  
2. 设非齐次解为 $\displaystyle y=C(x)\cdot e^{-\int p(x)dx}$  
3. 求导：$\displaystyle y'=C'(x)\cdot e^{-\int p(x)dx}-C(x)\cdot p(x)\cdot e^{-\int p(x)dx}$  
4. 代入原方程，化简得：
   $\displaystyle C'(x)\cdot e^{-\int p(x)dx}=q(x)$，即 $\displaystyle C'(x)=q(x)\cdot e^{\int p(x)dx}$  
5. 积分得 $\displaystyle C(x)=\int q(x)\cdot e^{\int p(x)dx}dx+C$  
6. 代回得非齐次通解。

**典型例题**（同上）

解方程 $y'-\dfrac{2}{x}y=x+2$

1. 齐次通解：$y=Cx^2$  
2. 设非齐次解：$y=C(x)\cdot x^2$  
3. 求导：$y'=C'(x)\cdot x^2+2C(x)\cdot x$  
4. 代入：
   $$C'(x)\cdot x^2+2C(x)\cdot x-\frac{2}{x}\cdot C(x)\cdot x^2=x+2$$
   化简得：$C'(x)\cdot x^2=x+2$，即 $\displaystyle C'(x)=\frac{1}{x}+\frac{2}{x^2}$  
5. 积分：$\displaystyle C(x)=\int\left(\frac{1}{x}+\frac{2}{x^2}\right)dx+C=\ln|x|-\frac{2}{x}+C$  
6. 代回得：$y=x^2\left(\ln|x|-\frac{2}{x}+C\right)=Cx^2+x^2\ln|x|-2x$

---

#### 方法三：公式法（求解首选）

**原理**：直接使用由积分因子法推导出的固定通解公式。

**通解公式**

- 以 $y$ 为因变量：
  $$\boldsymbol{y=e^{-\int p(x)dx}\left[\int q(x)e^{\int p(x)dx}dx+C\right]}$$
- 以 $x$ 为因变量：
  $$\boldsymbol{x=e^{-\int P(y)dy}\left[\int Q(y)e^{\int P(y)dy}dy+C\right]}$$

**解法步骤**

1. 将方程整理为标准形式，准确找出 $p(x)$ 和 $q(x)$（或 $P(y)$ 和 $Q(y)$）  
2. 计算指数部分的积分 $\displaystyle\int p(x)dx$  
3. 计算积分部分 $\displaystyle\int q(x)e^{\int p(x)dx}dx$  
4. 代入公式，整理得通解

**典型例题**（同上）

解方程 $y'-\dfrac{2}{x}y=x+2$

1. $p(x)=-\dfrac{2}{x}$，$q(x)=x+2$  
2. $\displaystyle\int p(x)dx=\int -\frac{2}{x}dx=-2\ln|x|$  
3. 积分部分：
   $$\int q(x)e^{\int p(x)dx}dx=\int (x+2)e^{-2\ln|x|}dx=\int (x+2)\cdot\frac{1}{x^2}dx=\ln|x|-\frac{2}{x}+C$$
4. 代入公式：
   $$y=e^{2\ln|x|}\left(\ln|x|-\frac{2}{x}+C\right)=x^2\left(\ln|x|-\frac{2}{x}+C\right)$$
5. 通解：$y=Cx^2+x^2\ln|x|-2x$

**使用公式法时的注意事项**：
- 必须先将方程写成 $y'$ 系数为 $1$ 的标准形式，否则 $p(x)$ 和 $q(x)$ 会识别错误。
- 指数积分 $\int p(x)dx$ 中可以省去常数 $C$，因为最终公式中已包含通解常数。
- 若 $\int q(x)e^{\int p(x)dx}dx$ 难以直接积分，可尝试分部积分或拆项处理。

---

#### 三种方法对比

| 方法 | 优点 | 缺点 | 适用场景 |
|---|---|---|---|
| 积分因子法 | 理解本质，每一步意义清晰 | 步骤稍多 | 适合推导和检查 |
| 常数变易法 | 体现通解结构思想 | 运算量大 | 基础阶段学习 |
| 公式法 | 速度最快，准确率高 | 需牢记公式 | 考试和平时作业首选 |

---

### 2.4 伯努利方程

- **识别特征**：形如 $\boldsymbol{y'+p(x)y=q(x)y^\alpha}$，其中 $\alpha\neq0,1$（$\alpha=0$ 即一阶线性，$\alpha=1$ 可分离变量）。
- **解法步骤**：
  1. 两边同除以 $y^\alpha$，得 $y^{-\alpha}y'+p(x)y^{1-\alpha}=q(x)$  
  2. 令 $\boldsymbol{z=y^{1-\alpha}}$，则 $\dfrac{dz}{dx}=(1-\alpha)y^{-\alpha}\dfrac{dy}{dx}$  
  3. 代入得 $\dfrac{1}{1-\alpha}\dfrac{dz}{dx}+p(x)z=q(x)$，整理为 $\boldsymbol{z'+(1-\alpha)p(x)z=(1-\alpha)q(x)}$（一阶线性）  
  4. 解出 $z$，代回 $z=y^{1-\alpha}$ 即得原方程通解。
- **典型例题**：解方程 $y'+\dfrac{y}{x}=y^2$

  **解**：$\alpha=2$，两边除以 $y^2$ 得：
  $$y^{-2}y'+\frac{1}{x}y^{-1}=1$$
  令 $z=y^{-1}$，则 $z'=-y^{-2}y'$，代入得：
  $$-z'+\frac{1}{x}z=1 \implies z'-\frac{1}{x}z=-1$$
  这是一阶线性方程，$p(x)=-\dfrac{1}{x}$，$q(x)=-1$  
  通解：
  $$\begin{aligned}
  z&=e^{\int\frac{1}{x}dx}\left[\int(-1)e^{-\int\frac{1}{x}dx}dx+C\right] \\
  &=x\left[\int(-1)\cdot\frac{1}{x}dx+C\right]=x(-\ln|x|+C)
  \end{aligned}$$
  代回 $z=y^{-1}$，得 $\dfrac{1}{y}=Cx-x\ln|x|$，故通解为：
  $$y=\frac{1}{x(C-\ln|x|)}$$

- **解题技巧**：
  - 伯努利方程的关键是正确识别 $\alpha$ 的值，然后直接套用换元 $z=y^{1-\alpha}$。
  - 换元后得到的一阶线性方程通常较简单，优先使用公式法求解。
  - 若 $\alpha>0$，注意 $y=0$ 是否是一个特解，有时会作为奇解出现。

---

### 2.5 全微分方程（恰当方程）与积分因子

- **定义**：若方程写成对称形式 $P(x,y)dx+Q(x,y)dy=0$ 后，满足
  $$\frac{\partial P}{\partial y}=\frac{\partial Q}{\partial x}$$
  则称为**全微分方程（恰当方程）**。此时存在二元函数 $u(x,y)$，使得
  $$du=Pdx+Qdy=0$$
  通解为 $u(x,y)=C$。

- **解法步骤**：
  1. 将方程写成 $Pdx+Qdy=0$，验证 $\dfrac{\partial P}{\partial y}=\dfrac{\partial Q}{\partial x}$。
  2. 若满足，用以下方法之一求 $u(x,y)$：
     - **偏积分法**：由 $\dfrac{\partial u}{\partial x}=P$ 对 $x$ 积分得 $u=\int Pdx+\varphi(y)$，再对 $y$ 求导并令其等于 $Q$，定出 $\varphi(y)$。
     - **线积分法**：$u(x,y)=\int_{x_0}^x P(x,y_0)dx+\int_{y_0}^y Q(x,y)dy$（起点可任选使积分简单的点）。
  3. 通解为 $u(x,y)=C$。

- **典型例题**：解方程 $(2xy+3x^2)dx+(x^2+2y)dy=0$

  **解**：$P=2xy+3x^2$，$Q=x^2+2y$  
  验证：$\dfrac{\partial P}{\partial y}=2x$，$\dfrac{\partial Q}{\partial x}=2x$，相等，是全微分方程。  
  求原函数：  
  由 $\dfrac{\partial u}{\partial x}=2xy+3x^2$，对 $x$ 积分得：
  $$u=x^2y+x^3+\varphi(y)$$
  对 $y$ 求导：$\dfrac{\partial u}{\partial y}=x^2+\varphi'(y)$，令其等于 $Q=x^2+2y$，得 $\varphi'(y)=2y$，故 $\varphi(y)=y^2$。  
  所以 $u(x,y)=x^2y+x^3+y^2$，通解为：
  $$x^2y+x^3+y^2=C$$

- **积分因子法**：若 $Pdx+Qdy=0$ 不满足恰当条件，有时可找到一个非零函数 $\mu(x,y)$，乘到方程两边后使
  $$\frac{\partial (\mu P)}{\partial y}=\frac{\partial (\mu Q)}{\partial x}$$
  则 $\mu$ 称为积分因子。常见情况：
  - 若 $\dfrac{P_y-Q_x}{Q}$ 只与 $x$ 有关，则 $\mu(x)=\exp\left(\int\frac{P_y-Q_x}{Q}dx\right)$；
  - 若 $\dfrac{Q_x-P_y}{P}$ 只与 $y$ 有关，则 $\mu(y)=\exp\left(\int\frac{Q_x-P_y}{P}dy\right)$；
  - 有时也可通过观察凑出积分因子，如 $\mu=x^m y^n$ 等形式。
  求出积分因子后，化为全微分方程求解。

- **典型例题**：解方程 $(y^2-6xy)dx+(3xy-6x^2)dy=0$

  **解**：$P=y^2-6xy$，$Q=3xy-6x^2$，
  $P_y=2y-6x$，$Q_x=3y-12x$，不相等，非恰当方程。  
  计算 $\dfrac{P_y-Q_x}{Q}=\dfrac{(2y-6x)-(3y-12x)}{3xy-6x^2}=\dfrac{6x-y}{3x(y-2x)}=-\dfrac{1}{3x}$（与 $y$ 无关），  
  积分因子 $\mu(x)=\exp\left(\int-\frac{1}{3x}dx\right)=x^{-1/3}$。  
  乘以 $\mu$ 后得全微分方程，再按恰当方程方法求解（略）。

- **解题技巧**：
  - 验证恰当方程时，先检查交叉偏导是否相等，若等则直接用偏积分法。
  - 求原函数时，起点选取 $(0,0)$ 或 $(0,1)$ 等使计算简单，若积分路径涉及奇点需绕开。
  - 寻找积分因子时，优先检验 $\frac{P_y-Q_x}{Q}$ 或 $\frac{Q_x-P_y}{P}$ 是否为一元函数；若不是，再尝试观察法。

---

## 三、高阶可降阶型微分方程

### 降阶思想核心总结

高阶方程中，若能通过变量代换降低阶数，则化为一阶或低阶方程求解。常见可降阶类型：

| 类型 | 特征 | 降阶换元 | 降阶后方程 |
|---|---|---|---|
| $y^{(n)}=f(x)$ | 只含 $x$ 和最高阶导数 | 直接逐次积分 | $y^{(n-1)}=\int f(x)dx$ |
| $y''=f(x,y')$ | 不显含 $y$ | 令 $p=y'$，则 $y''=p'$ | $p'=f(x,p)$ |
| $y''=f(y,y')$ | 不显含 $x$ | 令 $p=y'$，则 $y''=p\frac{dp}{dy}$ | $p\frac{dp}{dy}=f(y,p)$ |
| $y''=f(y')$ | 既不显含 $x$ 也不显含 $y$ | 两种方法均可，优先 $p'=f(p)$ | $p'=f(p)$ 或 $p\frac{dp}{dy}=f(p)$ |

**判别口诀**：纯 $x$ 直接积，缺 $y$ 用 $p'$，缺 $x$ 用 $p\frac{dp}{dy}$，既缺 $x$ 又缺 $y$ 优先 $p'$。

---

### 3.0 $y^{(n)}=f(x)$ 型（直接逐次积分）

- **识别特征**：方程中只含自变量 $x$ 和未知函数的 $n$ 阶导数，不含低阶导数及函数本身。
- **解法步骤**：
  1. 先积分一次：$y^{(n-1)}=\int f(x)dx+C_1$
  2. 逐次向下积分，每积一次增加一个新常数，共 $n$ 次积分后得到通解。
- **典型例题**：解方程 $y'''=e^{2x}$

  **解**：
  $$y''=\int e^{2x}dx=\frac{1}{2}e^{2x}+C_1$$
  $$y'=\int\left(\frac{1}{2}e^{2x}+C_1\right)dx=\frac{1}{4}e^{2x}+C_1x+C_2$$
  $$y=\int\left(\frac{1}{4}e^{2x}+C_1x+C_2\right)dx=\frac{1}{8}e^{2x}+\frac{C_1}{2}x^2+C_2x+C_3$$
  通解：$y=\dfrac{1}{8}e^{2x}+A x^2+Bx+C$（其中 $A=\frac{C_1}{2},\ B=C_2,\ C=C_3$）

---

### 3.1 $y''=f(x,y')$ 型（不显含未知函数 $y$）

- **识别特征**：方程中只出现 $x$、$y'$、$y''$，不出现 $y$。
- **解法步骤**：
  1. 换元：令 $\boldsymbol{p=y'}$，则 $y''=p'=\dfrac{dp}{dx}$
  2. 原方程降阶为一阶微分方程：$p'=f(x,p)$
  3. 解此一阶方程，得到 $p=\varphi(x,C_1)$
  4. 再积分一次：$y=\int\varphi(x,C_1)dx+C_2$，得到通解

- **典型例题**：解方程 $y''=y'+x$

  **解**：令 $p=y'$，则 $y''=p'$，方程变为：
  $$p'-p=x$$
  这是一阶线性方程，通解：
  $$\begin{aligned}
  p&=e^{\int1\,dx}\left[\int x e^{-\int1\,dx}dx+C_1\right] \\
  &=e^x\left[\int x e^{-x}dx+C_1\right] \\
  &=e^x\left(-x e^{-x}-e^{-x}+C_1\right) \\
  &=C_1e^x-x-1
  \end{aligned}$$
  即 $y'=C_1e^x-x-1$，再积分得通解：
  $$y=C_1e^x-\frac{1}{2}x^2-x+C_2$$

- **解题技巧**：换元后得到的一阶方程可能是线性、可分离变量或齐次型，按一阶方程的判别顺序处理。

---

### 3.2 $y''=f(y,y')$ 型（不显含自变量 $x$）

- **识别特征**：方程中只出现 $y$、$y'$、$y''$，不出现 $x$。
- **解法步骤**：
  1. 换元：令 $\boldsymbol{p=y'}$，将 $y''$ 转化为对 $y$ 的导数：
     $$y''=\frac{dp}{dx}=\frac{dp}{dy}\cdot\frac{dy}{dx}=p\frac{dp}{dy}$$
  2. 原方程降阶为一阶微分方程：$p\dfrac{dp}{dy}=f(y,p)$
  3. 解此一阶方程，得到 $p=\psi(y,C_1)$
  4. 分离变量并积分：$\displaystyle\int\frac{dy}{\psi(y,C_1)}=\int dx=x+C_2$，得到通解

- **典型例题**：解方程 $yy''-(y')^2=0$

  **解**：令 $p=y'$，则 $y''=p\dfrac{dp}{dy}$，代入得：
  $$y\cdot p\frac{dp}{dy}-p^2=0 \implies p\left(y\frac{dp}{dy}-p\right)=0$$
  分两种情况：
  1. $p=0$，即 $y'=0$，解得 $y=C$（常数解）
  2. $y\dfrac{dp}{dy}-p=0$，分离变量得 $\dfrac{dp}{p}=\dfrac{dy}{y}$

  积分得 $\ln|p|=\ln|y|+C_0$，即 $p=C_1y$（$C_1=\pm e^{C_0}$）

  即 $y'=C_1y$，分离变量积分得 $\ln|y|=C_1x+C_2'$

  通解为：$y=C_2e^{C_1x}$（$C_2=\pm e^{C_2'}$，包含了 $p=0$ 时的常数解）

- **解题技巧**：
  - 遇到 $p\left(y\frac{dp}{dy}-p\right)=0$ 这种乘积形式，要分别讨论 $p=0$ 和另一因式为零两种情况，避免漏解。
  - 换元后得到的 $p$ 关于 $y$ 的方程，通常可按一阶方程处理，注意此时自变量是 $y$ 而非 $x$。

---

### 3.3 $y''=f(y')$ 型（既不显含 $x$ 也不显含 $y$）

- **识别特征**：方程中只出现 $y'$ 和 $y''$，完全不出现 $x$ 和 $y$。
- **解法选择**：此类方程既属于不显含 $y$ 型，也属于不显含 $x$ 型，因此两种换元方式理论上均可使用，但通常优先选择 $p'=f(p)$ 路径，因为直接得到关于 $p$ 的一阶方程，求解更为简便。
- **解法步骤（推荐路径）**：
  1. 换元：令 $\boldsymbol{p=y'}$，则 $y''=p'=\dfrac{dp}{dx}$
  2. 原方程降阶为：$\dfrac{dp}{dx}=f(p)$，这是可分离变量的一阶方程
  3. 分离变量并积分：$\displaystyle\int\frac{dp}{f(p)}=\int dx=x+C_1$，解出 $p=\varphi(x,C_1)$
  4. 再积分一次：$y=\int\varphi(x,C_1)dx+C_2$，得到通解

- **备选路径**（有时更快捷）：
  1. 换元：令 $\boldsymbol{p=y'}$，则 $y''=p\dfrac{dp}{dy}$
  2. 原方程降阶为：$p\dfrac{dp}{dy}=f(p)$
  3. 若 $p\neq0$，得 $\dfrac{dp}{dy}=\dfrac{f(p)}{p}$，分离变量求解，得到 $p=\psi(y,C_1)$
  4. 再解 $y'=\psi(y,C_1)$，分离变量积分得通解

- **典型例题**：解方程 $y''=1+(y')^2$

  **解法一（推荐路径，不显含 $y$ 视角）**：  
  令 $p=y'$，则 $y''=p'$，方程变为：
  $$\frac{dp}{dx}=1+p^2$$
  分离变量：$\displaystyle\frac{dp}{1+p^2}=dx$  
  积分：$\displaystyle\int\frac{dp}{1+p^2}=\int dx$，得 $\arctan p=x+C_1$  
  即 $p=\tan(x+C_1)$，也就是 $y'=\tan(x+C_1)$  
  再积分：$\displaystyle y=\int\tan(x+C_1)dx=-\ln|\cos(x+C_1)|+C_2$  
  通解为：$y=-\ln|\cos(x+C_1)|+C_2$

  **解法二（备选路径，不显含 $x$ 视角）**：  
  令 $p=y'$，则 $y''=p\dfrac{dp}{dy}$，方程变为：
  $$p\frac{dp}{dy}=1+p^2$$
  分离变量：$\displaystyle\frac{p}{1+p^2}dp=dy$  
  积分：$\displaystyle\int\frac{p}{1+p^2}dp=\int dy$，得 $\dfrac{1}{2}\ln(1+p^2)=y+C_0$  
  整理：$1+p^2=C_1e^{2y}$（$C_1=e^{2C_0}$），即 $p=\pm\sqrt{C_1e^{2y}-1}$  
  再由 $y'=p$ 分离变量积分，结果与解法一等价（但运算稍繁）。

- **解题技巧**：
  - 遇到 $y''=f(y')$ 型，优先用 $p'=f(p)$ 路径，因为自变量是 $x$，最后直接对 $x$ 积分即可。
  - 若 $f(p)$ 中不含 $x$ 且 $p'=f(p)$ 积分后难以反解出 $p$，可尝试备选路径。
  - 注意 $y''=f(y')$ 实际上同时属于前两种类型，判别时不要遗漏。

---

## 四、$n$ 阶线性微分方程解的性质与结构（以二阶为例）

二阶线性微分方程标准形式：

- 齐次：$y''+p(x)y'+q(x)y=0$ …… ①
- 非齐次：$y''+p(x)y'+q(x)y=f(x)$ …… ②

### 4.1 叠加原理

若 $y_1^*(x)$ 是方程 $y''+p(x)y'+q(x)y=f_1(x)$ 的解，$y_2^*(x)$ 是方程 $y''+p(x)y'+q(x)y=f_2(x)$ 的解，则 $y_1^*(x)+y_2^*(x)$ 是方程 $y''+p(x)y'+q(x)y=f_1(x)+f_2(x)$ 的解。

**应用技巧**：当右端 $f(x)$ 是两项之和时，可分别对每一项求特解，然后相加。

### 4.2 齐次方程解的性质

- **定理1**：若 $y_1(x),y_2(x)$ 是齐次方程①的两个解，则 $C_1y_1(x)+C_2y_2(x)$ 也是①的解（$C_1,C_2$ 为任意常数）。
- **定理2**：若 $y_1(x),y_2(x)$ 是齐次方程①的两个线性无关的解，则 $y=C_1y_1(x)+C_2y_2(x)$ 是①的通解。
- **线性无关判定**：$\dfrac{y_1(x)}{y_2(x)}\neq$ 常数（若比值为常数则线性相关）
  - 例：$y_1=e^x$ 与 $y_2=e^{2x}$ 线性无关（$\dfrac{e^x}{e^{2x}}=e^{-x}\neq$ 常数）；$y_1=e^x$ 与 $y_2=2e^x$ 线性相关

### 4.3 非齐次方程解的性质

- **定理3**：若 $y^*(x)$ 是非齐次方程②的一个特解，$Y(x)$ 是对应齐次方程①的通解，则 $y=Y(x)+y^*(x)$ 是非齐次方程②的通解。
- **定理4**：若 $y_1^*(x),y_2^*(x)$ 是非齐次方程②的两个特解，则 $y_1^*(x)-y_2^*(x)$ 是对应齐次方程①的解。

**应用技巧**：已知非齐次方程的两个不同特解，可直接相减得到齐次方程的一个非零解，进而构造出齐次通解。对于高阶非齐次线性方程，也可使用常数变易法（拉格朗日常数变易法）构造特解，但通常优先使用待定系数法（见第五节）。

---

## 五、二阶常系数线性微分方程

### 5.1 齐次方程：$\boldsymbol{y''+py'+qy=0}$（$p,q$ 为常数）

- **解法：特征方程法**
  1. 写出特征方程：$\boldsymbol{\lambda^2+p\lambda+q=0}$（将 $y''$ 换为 $\lambda^2$，$y'$ 换为 $\lambda$，$y$ 换为 $1$）
  2. 求解特征方程的两个根 $\lambda_1,\lambda_2$
  3. 根据根的三种情况，写出通解：

| 特征根情况 | 通解形式 |
|---|---|
| 两个不同实根 $\lambda_1 \neq \lambda_2$ | $y=C_1e^{\lambda_1 x}+C_2e^{\lambda_2 x}$ |
| 两个相同实根 $\lambda_1=\lambda_2=\lambda$ | $y=(C_1+C_2x)e^{\lambda x}$ |
| 一对共轭复根 $\lambda_{1,2}=\alpha\pm i\beta$ | $y=e^{\alpha x}(C_1\cos\beta x+C_2\sin\beta x)$ |

- **典型例题**：
  1. 解方程 $y''-3y'+2y=0$  
     **解**：特征方程 $\lambda^2-3\lambda+2=0$，解得 $\lambda_1=1,\lambda_2=2$  
     通解：$y=C_1e^x+C_2e^{2x}$

  2. 解方程 $y''-4y'+4y=0$  
     **解**：特征方程 $\lambda^2-4\lambda+4=0$，解得 $\lambda_1=\lambda_2=2$  
     通解：$y=(C_1+C_2x)e^{2x}$

  3. 解方程 $y''+2y'+5y=0$  
     **解**：特征方程 $\lambda^2+2\lambda+5=0$，解得 $\lambda_{1,2}=-1\pm2i$  
     通解：$y=e^{-x}(C_1\cos2x+C_2\sin2x)$

- **解题技巧**：
  - 特征方程为二次方程，直接用求根公式或因式分解即可。
  - 重根情况容易遗漏 $x$ 因子，记忆口诀：重根多乘一个 $x$。
  - 复根情况下的 $\alpha$ 和 $\beta$ 要写清楚，$\alpha$ 来自实部，$\beta$ 来自虚部（取正）。

### 5.2 非齐次方程：$\boldsymbol{y''+py'+qy=f(x)}$

**通解结构**：$y=$ 齐次通解 $Y(x)+$ 非齐次特解 $y^*(x)$

**求特解思路**：根据 $f(x)$ 的形式直接设出特解类型，代入方程用待定系数法确定参数。

---

#### 类型1：$\boldsymbol{f(x)=P_m(x)e^{rx}}$

- $P_m(x)$ 是 $x$ 的 $m$ 次多项式，$r$ 是实数
- **特解设法**：设特解为 $\boldsymbol{y^*=x^k Q_m(x)e^{rx}}$
  - $Q_m(x)$ 是与 $P_m(x)$ 同次的待定多项式（$m$ 次，系数待定）
  - $k$ 的取值（与特征根比较）：
    - $r$ 不是特征根：$k=0$
    - $r$ 是单特征根：$k=1$
    - $r$ 是二重特征根：$k=2$
- **解法步骤**：
  1. 求对应齐次方程的通解 $Y(x)$
  2. 根据 $r$ 与特征根的关系设出特解 $y^*$
  3. 将 $y^*$ 代入原方程，比较系数求出待定系数
  4. 写出非齐次方程的通解 $y=Y(x)+y^*$

- **典型例题**：解方程 $y''-2y'-3y=3x+1$

  **解**：  
  1. 齐次通解：特征方程 $\lambda^2-2\lambda-3=0$，解得 $\lambda_1=-1,\lambda_2=3$  
     齐次通解：$Y=C_1e^{-x}+C_2e^{3x}$
  2. 设特解：$f(x)=(3x+1)e^{0x}$，$r=0$ 不是特征根，$k=0$  
     设 $y^*=ax+b$（一次多项式）
  3. 代入原方程：  
     $(ax+b)''-2(ax+b)'-3(ax+b)=3x+1$  
     $0-2a-3ax-3b=3x+1$  
     整理：$-3ax+(-2a-3b)=3x+1$  
     比较系数：
     $$\begin{cases} -3a=3 \\ -2a-3b=1 \end{cases} \quad\text{解得}\quad \begin{cases} a=-1 \\ b=\dfrac{1}{3} \end{cases}$$
     特解：$y^*=-x+\dfrac{1}{3}$
  4. 通解：$y=C_1e^{-x}+C_2e^{3x}-x+\dfrac{1}{3}$

- **解题技巧**：
  - $k$ 的取值关键是看 $r$ 与特征根的重合次数，不是特征根不加 $x$，单根乘 $x$，二重根乘 $x^2$。
  - 若 $P_m(x)$ 是常数（$m=0$），待定多项式就是一个常数 $a$。

---

#### 类型2：$\boldsymbol{f(x)=e^{\alpha x}[P_l(x)\cos\beta x+Q_m(x)\sin\beta x]}$

- $P_l(x)$ 是 $l$ 次多项式，$Q_m(x)$ 是 $m$ 次多项式，$\alpha,\beta$ 是实数
- **特解设法**：设特解为 $\boldsymbol{y^*=x^k e^{\alpha x}[M_n(x)\cos\beta x+N_n(x)\sin\beta x]}$
  - $n=\max\{l,m\}$，$M_n(x),N_n(x)$ 是两个 $n$ 次待定多项式
  - $k$ 的取值：
    - $\alpha\pm i\beta$ 不是特征根：$k=0$
    - $\alpha\pm i\beta$ 是特征根：$k=1$

- **典型例题**：解方程 $y''+y=x\cos2x$

  **解**：  
  1. 齐次通解：特征方程 $\lambda^2+1=0$，解得 $\lambda_{1,2}=\pm i$  
     齐次通解：$Y=C_1\cos x+C_2\sin x$
  2. 设特解：$f(x)=e^{0x}(x\cos2x+0\cdot\sin2x)$，$\alpha=0,\beta=2$  
     $\alpha\pm i\beta=\pm2i$ 不是特征根，$k=0$，$n=\max\{1,0\}=1$  
     设 $y^*=(ax+b)\cos2x+(cx+d)\sin2x$
  3. 求导代入原方程：  
     $$\begin{aligned}
     y^{*'} &= a\cos2x-2(ax+b)\sin2x+c\sin2x+2(cx+d)\cos2x \\
     &= (2cx+a+2d)\cos2x+(-2ax-2b+c)\sin2x \\[4pt]
     y^{*''} &= 2c\cos2x-2(2cx+a+2d)\sin2x-2a\sin2x+2(-2ax-2b+c)\cos2x \\
     &= (-4ax-4b+4c)\cos2x+(-4cx-4a-4d)\sin2x
     \end{aligned}$$
     代入 $y''+y=x\cos2x$：
     $$(-4ax-4b+4c+ax+b)\cos2x+(-4cx-4a-4d+cx+d)\sin2x=x\cos2x$$
     整理：
     $$(-3ax-3b+4c)\cos2x+(-3cx-4a-3d)\sin2x=x\cos2x$$
     比较系数：
     $$\begin{cases} -3a=1 \\ -3b+4c=0 \\ -3c=0 \\ -4a-3d=0 \end{cases} \quad\text{解得}\quad \begin{cases} a=-\dfrac{1}{3} \\[2pt] b=0 \\[2pt] c=0 \\[2pt] d=\dfrac{4}{9} \end{cases}$$
     特解：$y^*=-\dfrac{1}{3}x\cos2x+\dfrac{4}{9}\sin2x$
  4. 通解：$y=C_1\cos x+C_2\sin x-\dfrac{1}{3}x\cos2x+\dfrac{4}{9}\sin2x$

- **解题技巧**：
  - 即使 $f(x)$ 中只有 $\cos$ 或只有 $\sin$，设特解时也要同时设出 $\cos$ 和 $\sin$ 两项。
  - $n$ 取 $l$ 和 $m$ 的最大值，待定多项式按最高次项写完整。
  - 求导计算量较大时，可先对各项求导再合并同类项，避免遗漏。
  - 系数比较时，等式两边 $\cos\beta x$ 和 $\sin\beta x$ 的系数各自相等。

---

## 六、高阶常系数线性齐次微分方程

- **一般形式**：$y^{(n)}+a_1y^{(n-1)}+\dots+a_{n-1}y'+a_ny=0$（$a_1,\dots,a_n$ 为常数）
- **解法：特征方程法**
  1. 写出特征方程：$\lambda^n+a_1\lambda^{n-1}+\dots+a_{n-1}\lambda+a_n=0$
  2. 求解特征根，根据根的类型写出对应通解项：

| 特征根类型 | 对应通解中的项 |
|---|---|
| 单实根 $\lambda$ | $Ce^{\lambda x}$ |
| $k$ 重实根 $\lambda$ | $(C_1+C_2x+\cdots+C_k x^{k-1})e^{\lambda x}$ |
| 单共轭复根 $\alpha\pm i\beta$ | $e^{\alpha x}(C_1\cos\beta x+C_2\sin\beta x)$ |
| $k$ 重共轭复根 $\alpha\pm i\beta$ | $e^{\alpha x}\big[(C_1+C_2x+\cdots+C_k x^{k-1})\cos\beta x + (D_1+D_2x+\cdots+D_k x^{k-1})\sin\beta x\big]$ |

  3. 所有特征根对应的项相加，得到通解

- **典型例题**：解方程 $y'''-3y''+3y'-y=0$

  **解**：特征方程 $\lambda^3-3\lambda^2+3\lambda-1=0$，即 $(\lambda-1)^3=0$  
  有三重实根 $\lambda=1$  
  通解：$y=(C_1+C_2x+C_3x^2)e^x$

- **解题技巧**：
  - 高阶特征方程的因式分解是关键，注意观察是否能用完全立方公式、平方差等分解。
  - 重根时，每多一重就多乘一个 $x$ 的更高次幂。
  - 复根总是成对出现，每对复根对应两项（$\cos$ 和 $\sin$）。

- **非齐次高阶常系数线性方程**：当方程为 $y^{(n)}+a_1y^{(n-1)}+\dots+a_ny=f(x)$ 时，通解仍为齐次通解加特解。特解形式可仿照二阶进行推广，例如 $f(x)=P_m(x)e^{rx}$ 时，设 $y^*=x^k Q_m(x)e^{rx}$，$k$ 为 $r$ 作为特征根的重数（$k$ 可为 $0,1,\dots,n$）。也可使用算子法或拉格朗日常数变易法，但待定系数法最为常用。

---

## 七、欧拉方程

- **定义**：形如 $\boldsymbol{x^n y^{(n)}+a_1x^{n-1}y^{(n-1)}+\dots+a_{n-1}xy'+a_ny=f(x)}$ 的方程（$a_1,\dots,a_n$ 为常数）
- **解法步骤**（变量替换法）：
  1. 当 $x>0$ 时，令 $\boldsymbol{x=e^t}$（即 $t=\ln x$）；当 $x<0$ 时，令 $x=-e^t$，类似处理。
  2. 引入微分算子 $D=\dfrac{d}{dt}$，则各阶导数可表示为：
     $$\begin{aligned}
     xy' &= Dy \\
     x^2y'' &= D(D-1)y \\
     x^3y''' &= D(D-1)(D-2)y \\
     &\ \vdots \\
     x^k y^{(k)} &= D(D-1)\cdots(D-k+1)y
     \end{aligned}$$
  3. 代入原方程，转化为以 $t$ 为自变量的常系数线性微分方程。
  4. 求解常系数方程（齐次或非齐次），得到通解 $y(t)$。
  5. 代回 $t=\ln|x|$，得到原方程的通解。

- **齐次欧拉方程典型例题**：解方程 $x^2y''+xy'-y=0$

  **解**：令 $x=e^t$，$t=\ln x$，则：
  $$xy'=Dy,\quad x^2y''=D(D-1)y$$
  代入原方程：
  $$D(D-1)y+Dy-y=0$$
  整理：$(D^2-1)y=0$，即 $\dfrac{d^2y}{dt^2}-y=0$  
  特征方程 $\lambda^2-1=0$，解得 $\lambda_1=1,\lambda_2=-1$  
  通解：$y=C_1e^t+C_2e^{-t}$  
  代回 $t=\ln x$，原方程通解：$y=C_1x+\dfrac{C_2}{x}$

- **非齐次欧拉方程的处理**：  
  若 $f(x)\neq0$，作变换 $x=e^t$ 后，方程变为常系数非齐次线性方程，右端变为 $f(e^t)$。此时按常系数非齐次方程的方法（待定系数法）求出特解即可。  
  **例**：$x^2y''+xy'-y=x^2$，令 $x=e^t$ 化为 $D(D-1)y+Dy-y=e^{2t}$，即 $(D^2-1)y=e^{2t}$，右端为指数函数 $e^{2t}$，设特解 $y^*=Ae^{2t}$ 代入可解得 $A=\frac{1}{3}$，故特解 $y^*=\frac{1}{3}x^2$，齐次通解如上，通解 $y=C_1x+\frac{C_2}{x}+\frac{1}{3}x^2$。

- **解题技巧**：
  - 欧拉方程的标志是每一项中 $x$ 的幂次与 $y$ 的导数阶数一致。
  - 微分算子 $D(D-1)$ 等展开后直接

作为常系数处理，无需额外推导。
  - 最终结果中 $e^{kt}$ 换回 $x^k$，$e^{\alpha t}\cos(\beta t)$ 换回 $x^\alpha\cos(\beta\ln x)$ 等形式。