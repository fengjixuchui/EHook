# EHook

A hooking framework for Commercial Android Emulator ([雷电模拟器](http://www.ldmnq.com/), [NOX](https://jp.bignox.com/))


# Usage

1. Modify the jni/realinject.c file. You can hook functions both by address or by the function's name:

```
    static struct hook_t eph1;
    static struct hook_t eph_sendto;
    ...
    ...
    
    hook_by_addr(&eph1, "libc.so", target_addr, hook_func1);
    
    hook_by_name(&eph_sendto, "libc.so", "sendto", hook_sendto);
```
    
2. Run `ndk-build`

3. Push the following 3 binary to android /data/local/tmp directory: 
    `libs/x86/stalker` 
    `libs/x86/libinject.so`
    `libs/armeabi/librealinject.so`

Or just run `sh push.sh` if you are on *nix system.

4. On android, type `./stalker [pid]`.

# Notice
For NOX emulator, you should use the Android 5.1.1 instead of the default 4.4.2.
