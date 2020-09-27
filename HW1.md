### HW1

2.4
(c)
$$\begin{aligned}
    &\bold{dict0} \rightarrow A|B|... \qquad 省略号中包含除了*以外该语言的所有字符 \\
    &\bold{dict1} \rightarrow A|B|... \qquad 省略号中包含除了*和/以外该语言的所有字符 \\
    &\bold{string0} \rightarrow *^{+} \bold{dict1} \bold{dict0}^{*} \qquad \bold{string0}为当字符串中有/和*时构造的约束(不允许出现*/) \\
    &\bold{annotation} \rightarrow /* \bold{dict0}^{*} \bold{string0}^{*} *^{*} */ \\&确保/**/中的字符的串四种情况:是否以*开头，以及是否以*结尾 \\
    &以*开头:\bold{string0}中的*^{+};不以*开头:\bold{annotation}中的\bold{dict0}^{*} \\
    &以*结尾:\bold{annotation}中的*^{*};不以*结尾:\bold{string0}中的\bold{dict0}^{*} \\
\end{aligned}$$

(d)
$$\begin{aligned}
    &\bold{no\_1-9} \rightarrow 0 \\
    &\bold{no\_1-9}表示所有不含[1-9]中数字,且相邻数字都不同的非空串(其余以此类推) \\
    &\bold{no\_2-9} \rightarrow 1 \quad | \quad \bold{no\_1-9} \quad | \quad 1?(\bold{no\_1-9} \quad 1)^{+} \bold{no\_1-9}? \\
    &\bold{no\_2-9}从1,\bold{no\_1-9},以及新构造的串中选择 \\
    &新构造的串有4种情况,是否以1开头以及是否以1结尾 \\
    &其余情况以此类推 \\
    &\bold{no\_3-9} \rightarrow 2 \quad | \quad \bold{no\_2-9} \quad | \quad 2?(\bold{no\_2-9} \quad 2)^{+} \bold{no\_2-9}? \\
    &\bold{no\_4-9} \rightarrow 3 \quad | \quad \bold{no\_3-9} \quad | \quad 3?(\bold{no\_3-9} \quad 3)^{+} \bold{no\_3-9}? \\
    &\bold{no\_5-9} \rightarrow 4 \quad | \quad \bold{no\_4-9} \quad | \quad 4?(\bold{no\_4-9} \quad 4)^{+} \bold{no\_4-9}? \\
    &\bold{no\_6-9} \rightarrow 5 \quad | \quad \bold{no\_5-9} \quad | \quad 5?(\bold{no\_5-9} \quad 5)^{+} \bold{no\_5-9}? \\
    &\bold{no\_7-9} \rightarrow 6 \quad | \quad \bold{no\_6-9} \quad | \quad 6?(\bold{no\_6-9} \quad 6)^{+} \bold{no\_6-9}? \\
    &\bold{no\_8-9} \rightarrow 7 \quad | \quad \bold{no\_7-9} \quad | \quad 7?(\bold{no\_7-9} \quad 7)^{+} \bold{no\_7-9}? \\
    &\bold{no\_9} \rightarrow 8 \quad | \quad \bold{no\_8-9} \quad | \quad 8?(\bold{no\_8-9} \quad 8)^{+} \bold{no\_8-9}? \\
    &\bold{answer} \rightarrow 9 \quad | \quad \bold{no\_9} \quad | \quad 9?(\bold{no\_9} \quad 9)^{+} \bold{no\_9}? \\
\end{aligned}$$

2.7
(d)
![识别$(a|b)^{*}abb(a|b)^{*}$的NFA](figs/2.7_d.png)
<center>图1 识别(a|b)<sup>*</sup>abb(a|b)<sup>*</sup>的NFA</center>

$$\begin{aligned}
    &当输入串为ababbab时,状态转换序列为 \\
    &0 \stackrel{\epsilon}{\rightarrow} 1 \stackrel{\epsilon}{\rightarrow} 2 \stackrel{a}{\rightarrow} 3 \stackrel{\epsilon}{\rightarrow} 6 \stackrel{\epsilon}{\rightarrow} 1 \stackrel{\epsilon}{\rightarrow} 4 \stackrel{b}{\rightarrow} 5 \stackrel{\epsilon}{\rightarrow} 6 \stackrel{\epsilon}{\rightarrow} 7 \stackrel{a}{\rightarrow} 8 \stackrel{b}{\rightarrow} 9 \\
    &\stackrel{b}{\rightarrow} 10 \stackrel{\epsilon}{\rightarrow} 11 \stackrel{\epsilon}{\rightarrow} 12 \stackrel{a}{\rightarrow} 13 \stackrel{\epsilon}{\rightarrow} 16 \stackrel{\epsilon}{\rightarrow} 11 \stackrel{\epsilon}{\rightarrow} 14 \stackrel{b}{\rightarrow} 15 \stackrel{\epsilon}{\rightarrow} 16 \stackrel{\epsilon}{\rightarrow} 17
\end{aligned}$$

2.8
(2.7对应部分)
$$\begin{aligned}
    &记A=\epsilon-closure(0)=\{0,1,2,4,7\} \\
    &则B=\epsilon-closure(move(A,a))=\epsilon-closure(\{3,8\})=\{1,2,3,4,6,7,8\} \\
    &记C=\epsilon-closure(move(A,b))=\epsilon-closure(\{5\})=\{1,2,4,5,6,7\} \\
    &\epsilon-closure(move(B,a))=\epsilon-closure(\{3,8\})=B \\
    &记D=\epsilon-closure(move(B,b))=\epsilon-closure(\{5,9\})=\{1,2,4,5,6,7,9\} \\
    &\epsilon-closure(move(C,a))=\epsilon-closure(\{3,8\})=B \\
    &\epsilon-closure(move(C,b))=\epsilon-closure(\{5\})=C \\
    &\epsilon-closure(move(D,a))=\epsilon-closure(\{3,8\})=B \\
    &记E=\epsilon-closure(move(D,b))=\epsilon-closure(\{5,10\})=\{1,2,4,5,6,7,10,11,12,14,17\} \\
    &记F=\epsilon-closure(move(E,a))=\epsilon-closure(\{3,8,13\})=\{1,2,3,4,6,7,8,11,12,13,14,16,17\} \\
    &记G=\epsilon-closure(move(E,b))=\epsilon-closure(\{5,15\})=\{1,2,4,5,6,7,11,12,14,15,16,17\} \\
    &\epsilon-closure(move(F,a))=\epsilon-closure(\{3,8,13\})=F \\
    &记H=\epsilon-closure(move(F,b))=\epsilon-closure(\{5,9,15\})=\{1,2,4,5,6,7,9,11,12,14,15,16,17\} \\
    &\epsilon-closure(move(G,a))=\epsilon-closure(\{3,8,13\})=F \\
    &\epsilon-closure(move(G,b))=\epsilon-closure(\{5,15\})=G \\
    &\epsilon-closure(move(H,a))=\epsilon-closure(\{3,8,13\})=F \\
    &记I=\epsilon-closure(move(H,b))=\epsilon-closure(\{5,10,15\})=\{1,2,4,5,6,7,10,11,12,14,15,16,17\} \\
    &\epsilon-closure(move(I,a))=\epsilon-closure(\{3,8,13\})=F \\
    &\epsilon-closure(move(I,b))=\epsilon-closure(\{5,15\})=G \\
\end{aligned}$$

$$\begin{aligned}
    \begin{array}{c|c|c}
        \hline
        状态 & 输入符号 & 输入符号 \\
        & a  & b \\
        \hline
        A & B & C \\
        \hline
        B & B & D \\
        \hline
        C & B & C \\
        \hline
        D & B & E \\
        \hline
        E & F & G \\
        \hline
        F & F & H \\
        \hline
        G & F & G \\
        \hline
        H & F & I \\
        \hline
        I & F & G \\
        \hline
    \end{array} \\
    表1 \quad 2.8(d)DFA的转换表Dtran \\
\end{aligned}$$

![识别$(a|b)^{*}abb(a|b)^{*}$的DFA](figs/2.8_d.png)
<center>图2 识别(a|b)<sup>*</sup>abb(a|b)<sup>*</sup>的DFA</center>

$$\begin{aligned}
    当输入串为ababbab时,状态转换序列为A \stackrel{a}{\rightarrow} B \stackrel{b}{\rightarrow} D \stackrel{a}{\rightarrow} B \stackrel{b}{\rightarrow} D \stackrel{b}{\rightarrow} E \stackrel{a}{\rightarrow} F \stackrel{b}{\rightarrow} H \\
\end{aligned}$$

2.12
(b)
![识别$(a|b)^{*}a(a|b)(a|b)$的NFA](figs/2.12_b_NFA.png)
<center>图3 识别(a|b)<sup>*</sup>a(a|b)(a|b)的NFA</center>

$$\begin{aligned}
    &记A=\epsilon-closure(0)=\{0,1,2,4,7\} \\
    &则B=\epsilon-closure(move(A,a))=\epsilon-closure(\{3,8\})=\{1,2,3,4,6,7,8,9,11\} \\
    &记C=\epsilon-closure(move(A,b))=\epsilon-closure(\{5\})=\{1,2,4,5,6,7\} \\
    &记D=\epsilon-closure(move(B,a))=\epsilon-closure(\{3,8,10\})=\{1,2,3,4,6,7,8,9,10,11,13,14,16\} \\
    &记E=\epsilon-closure(move(B,b))=\epsilon-closure(\{5,12\})=\{1,2,4,5,6,7,12,13,14,16\} \\
    &\epsilon-closure(move(C,a))=\epsilon-closure(\{3,8\})=B \\
    &\epsilon-closure(move(C,b))=\epsilon-closure(\{5\})=C \\
    &记F=\epsilon-closure(move(D,a))=\epsilon-closure(\{3,8,10,15\})=\{1,2,3,4,6,7,8,9,10,11,13,14,15,16,18\} \\
    &记G=\epsilon-closure(move(D,b))=\epsilon-closure(\{5,12,17\})=\{1,2,4,5,6,7,12,13,14,16,17,18\} \\
    &记H=\epsilon-closure(move(E,a))=\epsilon-closure(\{3,8,15\})=\{1,2,3,4,6,7,8,9,11,15,18\} \\
    &记I=\epsilon-closure(move(E,b))=\epsilon-closure(\{5,17\})=\{1,2,4,5,6,7,17,18\} \\
    &\epsilon-closure(move(F,a))=\epsilon-closure(\{3,8,10,15\})=F \\
    &\epsilon-closure(move(F,b))=\epsilon-closure(\{5,12,17\})=G \\
    &\epsilon-closure(move(G,a))=\epsilon-closure(\{3,8,15\})=H \\
    &\epsilon-closure(move(G,b))=\epsilon-closure(\{5,17\})=I \\
    &\epsilon-closure(move(H,a))=\epsilon-closure(\{3,8,10\})=D \\
    &\epsilon-closure(move(H,b))=\epsilon-closure(\{5,12\})=E \\
    &\epsilon-closure(move(I,a))=\epsilon-closure(\{3,8\})=B \\
    &\epsilon-closure(move(I,b))=\epsilon-closure(\{5\})=C \\
\end{aligned}$$

$$\begin{aligned}
    \begin{array}{c|c|c}
        \hline
        状态 & 输入符号 & 输入符号 \\
        & a  & b \\
        \hline
        A & B & C \\
        \hline
        B & D & E \\
        \hline
        C & B & C \\
        \hline
        D & F & G \\
        \hline
        E & H & I \\
        \hline
        F & F & G \\
        \hline
        G & H & I \\
        \hline
        H & D & E \\
        \hline
        I & B & C \\
        \hline
    \end{array} \\
    表2 \quad 2.12(b)DFA的转换表Dtran \\
\end{aligned}$$

$$\begin{aligned}
    &由图3和表2可知,F,G,H,I为接受状态,A与C不可区别 \\
    &化简后可得最简的DFA转换表Dtran_{new}(将状态从[A-I]换为[0-7]) \\
    &A=C=0,B=1,D=2,E=3,F=4,G=5,H=6,I=7 \\
\end{aligned}$$

$$\begin{aligned}
    \begin{array}{c|c|c}
        \hline
        状态 & 输入符号 & 输入符号 \\
        & a  & b \\
        \hline
        0 & 1 & 0 \\
        \hline
        1 & 2 & 3 \\
        \hline
        2 & 4 & 5 \\
        \hline
        3 & 6 & 7 \\
        \hline
        4 & 4 & 5 \\
        \hline
        5 & 6 & 7 \\
        \hline
        6 & 2 & 3 \\
        \hline
        7 & 1 & 0 \\
        \hline
    \end{array} \\
    表3 \quad 最简的DFA转换表Dtran_{new} \\
\end{aligned}$$

![识别$(a|b)^{*}a(a|b)(a|b)$的NFA](figs/2.12_b_DFA.png)
<center>图4 识别(a|b)<sup>*</sup>a(a|b)(a|b)的DFA</center>
