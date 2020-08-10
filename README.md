# libgrpc_csharp_ext_arm64
This is a prebuilt binary of https://github.com/erikest/libgrpc_csharp_ext with target ARM64 (aarch64), version 1.31.0

I'm developing an application on the NVIDIA Jetson Nano with .net core and grpc. Since grpc doesn't really support ARM as of now, I have to build the native libraries myself. 

You may wonder why the binary is named *x64*:
- https://github.com/grpc/grpc/blob/a339a13591cb1fab70abe41ffa03a31d1b196eab/src/csharp/Grpc.Core/Internal/NativeExtension.cs#L98 the PInvoke calls will look for a file named "x64" *regardless* of the architecture (after all, x64 itself isn't really even the real correct identifier for 64-bit systems -- it's just so convienent to use the term indiscriminately. Even Microsoft names their DLL "AMD64" for 64 bit and "x86" for 32 bits. In fact, it is Intel64/EM64T/AMD64 depending on the manufacturer and time).
- grpc doesn't factor in the architecture, because their main focus is x86 (they explicitly stated in the link above). It only cares about the platform (linux, win, macosx).
