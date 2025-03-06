# a_m_audit
# 简介
一个用于静态分析和漏洞审计的工具，主要用于帮助分析程序中的潜在安全问题和弱点。该插件的作用是对目标程序进行深度审计，查找可能的漏洞，如缓冲区溢出、格式化字符串漏洞、未经授权的访问控制等。同时支持ARM与MIPS架构的二进制文件分析。

# 功能

1. **自动化漏洞检测：** 插件会自动分析目标二进制文件，通过静态分析技术检查潜在的漏洞点。
    
2. **函数检查：** 它可以检测到常见的漏洞函数，像 `strcpy`、`gets`、`scanf` 等，这些函数通常是导致安全漏洞的根源。
    
3. **符号解析：** 插件能够处理二进制文件中的符号信息，帮助分析执行流程，并查找可能被滥用的功能。

双击函数地址，可以跳转到对应位置

![image](https://github.com/user-attachments/assets/d2ca9f11-8d65-4fbc-857d-e629e1946d53)

![image](https://github.com/user-attachments/assets/49c8804a-c27d-453a-a961-417b8fb6ff88)


# 扫描的危险函数

自己根据需要增加了一些........
```
# set function_name
dangerous_functions = [
    "strcpy", "strcat", "sprintf", "read", "getenv",
    "gets", "scanf", "vsprintf", "strnlen", "wcscpy"
]

attention_function = [
    "memcpy", "malloc", "strncpy", "sscanf", "strncat", "snprintf", "vprintf", "printf",
    "memset", "free", "strlen", "wcsncpy", "vfscanf"
]

command_execution_function = [
    "system", "execve", "popen", "unlink", "dosystem",
    "execl", "execvp", "remove", "rename", "fork"
]

# describe arg num of function
one_arg_function = [
    "malloc", "getenv", "system", "unlink", "dosystem",
    "gets", "free", "strlen", "remove"
]

two_arg_function = [
    "strcpy", "strcat", "popen",
    "wcscpy", "rename"
]

three_arg_function = [
    "strncpy", "strncat", "memcpy", "execve", "read",
    "memset", "wcsncpy", "strnlen"
]

format_function_offset_dict = {
    "sprintf": 1, "sscanf": 1, "snprintf": 2, "vprintf": 0, "printf": 0,
    "vsprintf": 1, "scanf": 0, "vfscanf": 1
}
```

# 安装
a_m_audit.py -> plugins

![image](https://github.com/user-attachments/assets/0178d357-786f-4137-95b3-7701d706c65a)
