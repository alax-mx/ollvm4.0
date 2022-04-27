使用说明：
1， 将clang、clang++、clang-format替换掉
     android-ndk-r21d\toolchains\llvm\prebuilt\windows-x86_64\bin文件夹中的同名文件

2，将lib文件夹中的文件复制到
     android-ndk-r21d\toolchains\llvm\prebuilt\windows-x86_64\lib文件夹中

3，删除ndk中的\toolchains\llvm\prebuilt\windows-x86_64\lib64

4, 在Android.mk 中新增
     LOCAL_CFLAGS += -mllvm -sub -mllvm -bcf -mllvm -fla -mllvm -sobf (这里是所有函数都混淆) 
   或者在需要的函数前面加上：
    __attribute__((__annotate__(("sub bcf fla"))))

   -mllvm -sobf 是混淆字符串