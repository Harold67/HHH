# HHH
Code for the project
graph TD;
    A[开始] --> B[读取命令信息];
    B --> C{命令码};
    C -- 0xEA --> D[处理0xEA命令];
    C -- 0xCA --> E[处理0xCA命令];
    C -- 其他 --> F[处理其他命令];
    D --> G[发送0xEA命令];
    G --> H{是否超时};
    H -- 是 --> I[返回错误];
    H -- 否 --> J{发送成功};
    J -- 是 --> K[等待擦除完成];
    K -- 超时 --> L[返回错误];
    K -- 完成 --> M[返回成功];
    E --> N{是否准备好擦除};
    N -- 否 --> O[返回错误];
    N -- 是 --> P[发送数据];
    P --> Q{是否超时};
    Q -- 是 --> R[返回错误];
    Q -- 否 --> S{发送成功};
    S -- 是 --> T[等待写入完成];
    T -- 超时 --> U[返回错误];
    T -- 完成 --> V[返回成功];
    F --> W[发送其他命令];
    W --> X{是否超时};
    X -- 是 --> Y[返回错误];
    X -- 否 --> Z{发送成功};
    Z -- 是 --> AA[返回成功];
    AA -- 否 --> AB[返回错误];
    AB --> Z;
    L --> AB;
    U --> AB;
    Y --> AB;
    AB --> 结束;
