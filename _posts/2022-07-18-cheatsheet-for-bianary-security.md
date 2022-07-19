# Executing shell code remotely (2022-07-18)

## Docker commands
- Show all containers: `docker ps -a`
- `0.0.0.0:60001->9999/tcp` means expose container 9999 to host's 60001.

## GDB Commands:
- Install GDB plugins: 

```sh 
cd ~/
git clone https://github.com/longld/peda.git ~/peda
git clone https://github.com/scwuaptx/Pwngdb.git
cp ~/Pwngdb/.gdbinit ~/
```

- Finish current function: `finish`.
- For SEGV, look into Code to dertermine what was accessed illegally, and look into registers to verify.
- To step by one, use `si`.

## Syscall
- `rax` is the syscall [number][1] and the location of the return value.
- The first three parameters of syscall are `rdi, rsi, rdx`
- A negative return value means it failed.
- To store a string in stack, we can use: 


```sh
mov rdi, {hex of the string, little endian}
push rdi
mov rdi, rsp
```


## Misc
- In order to split the terminal, we need to use `tmux` in wsl.
- To run a binary without ASLR: `p = process("./chal1",aslr=0)`


[1]: https://syscalls64.paolostivanin.com/