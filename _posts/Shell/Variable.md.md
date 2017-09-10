-   [Linux Shell 编程之变量](#orgedf4edf)
    -   [shellscript-变量的定义](#org84a423f)
        -   [通用](#org525869b)
        -   [bash](#orgc306ef0)

<a id="orgedf4edf"></a>

&ensp;&ensp; 在一门编程语言中，变量是不可缺少的元素，如果将程序比作是房子的话，那么变量就是构成房子的砖石。

<a id="org84a423f"></a>

\## shellscript-变量的定义

<a id="org525869b"></a>

\### 通用

\`\`\`shell a='test' \`\`\`

&ensp&ensp; 上面的代码中，定义了一个 \`a\` 变量，并将字符串 \`test\` 传递给变量 \`a\`. \`shellscript\` 的变量 \`定义\` 和 \`赋值\` 是不需要 \`类型修饰符号(int,double,&#x2026;)\` 和 \`变量符号($,var,&#x2026;)\` 的。

<a id="orgc306ef0"></a>

\### bash

\`\`\`shell let a='test' \`\`\`

\`\`\`shell declare a='test' \`\`\`
