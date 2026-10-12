#!/usr/bin/env python

Import("env")

env.Append(CPPPATH=[Dir("..")])

enet_env = env.Clone()

if env.get("platform", env["PLATFORM"]) in ("windows", "win32"):
    env.Append(LIBS=["ws2_32", "winmm"])
    enet_env.Append(CPPDEFINES=["_WINSOCK_DEPRECATED_NO_WARNINGS"])
else:
    enet_env.Append(CPPDEFINES=["HAS_SOCKLEN_T", "HAS_POLL", "HAS_FCNTL", "HAS_GETADDRINFO",
                                "HAS_GETNAMEINFO", "HAS_INET_PTON", "HAS_INET_NTOP", "HAS_MSGHDR_FLAGS"])

if env["CC"] == "cl":
    enet_env.Append(CCFLAGS=["/wd5287"])

objects = enet_env.SharedObject(enet_env.Glob("*.c"))

Return("objects")