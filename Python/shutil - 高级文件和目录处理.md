# Shutil - 高级文件和目录处理

## 目录和文件操作

#### shutil.copytree(*src*, *dst*, *symlinks=False*, *ignore=None*, *copy_function=copy2*, *ignore_dangling_symlinks=False*, *dirs_exist_ok=False*)

将以 *src* 为根起点的整个目录树拷贝到名为 *dst* 的目录并返回目标目录。 *dirs_exist_ok* 指明是否要在 *dst* 或任何丢失的父目录已存在的情况下引发异常。

目录的权限和时间会通过 [`copystat()`](https://docs.python.org/zh-cn/3/library/shutil.html?highlight=copytree#shutil.copystat) 来拷贝，单个文件则会使用 [`copy2()`](https://docs.python.org/zh-cn/3/library/shutil.html?highlight=copytree#shutil.copy2) 来拷贝。

如果 *symlinks* 为真值，源目录树中的符号链接会在新目录树中表示为符号链接，并且原链接的元数据在平台允许的情况下也会被拷贝；如果为假值或省略，则会将被链接文件的内容和元数据拷贝到新目录树。

当 *symlinks* 为假值时，如果符号链接所指向的文件不存在，则会在拷贝进程的末尾将一个异常添加到 [`Error`](https://docs.python.org/zh-cn/3/library/shutil.html?highlight=copytree#shutil.Error) 异常中的错误列表。 如果你希望屏蔽此异常那就将可选的 *ignore_dangling_symlinks* 旗标设为真值。 请注意此选项在不支持 [`os.symlink()`](https://docs.python.org/zh-cn/3/library/os.html#os.symlink) 的平台上将不起作用。

如果给出了 *ignore*，它必须是一个可调用对象，该对象将接受 [`copytree()`](https://docs.python.org/zh-cn/3/library/shutil.html?highlight=copytree#shutil.copytree) 所访问的目录以及 [`os.listdir()`](https://docs.python.org/zh-cn/3/library/os.html#os.listdir) 所返回的目录内容列表作为其参数。 由于 [`copytree()`](https://docs.python.org/zh-cn/3/library/shutil.html?highlight=copytree#shutil.copytree) 是递归地被调用的，*ignore* 可调用对象对于每个被拷贝目录都将被调用一次。 该可调用对象必须返回一个相对于当前目录的目录和文件名序列（即其第二个参数的子集）；随后这些名称将在拷贝进程中被忽略。 [`ignore_patterns()`](https://docs.python.org/zh-cn/3/library/shutil.html?highlight=copytree#shutil.ignore_patterns) 可被用于创建这种基于 glob 风格模式来忽略特定名称的可调用对象。

如果发生了（一个或多个）异常，将引发一个附带原因列表的 [`Error`](https://docs.python.org/zh-cn/3/library/shutil.html?highlight=copytree#shutil.Error)。

如果给出了 *copy_function*，它必须是一个将被用来拷贝每个文件的可调用对象。 它在被调用时会将源路径和目标路径作为参数传入。 默认情况下，[`copy2()`](https://docs.python.org/zh-cn/3/library/shutil.html?highlight=copytree#shutil.copy2) 将被使用，但任何支持同样签名（与 [`copy()`](https://docs.python.org/zh-cn/3/library/shutil.html?highlight=copytree#shutil.copy) 一致）都可以使用。

引发一个 [审计事件](https://docs.python.org/zh-cn/3/library/sys.html#auditing) `shutil.copytree` 附带参数 `src`, `dst`。

*在 3.3 版更改:* 当 *symlinks* 为假值时拷贝元数据。 现在会返回 *dst*。

*在 3.2 版更改:* 添加了 *copy_function* 参数以允许提供定制的拷贝函数。 添加了 *ignore_dangling_symlinks* 参数以便在 *symlinks* 为假值时屏蔽符号链接错误。

*在 3.8 版更改:* 可能会在内部使用平台专属的快速拷贝系统调用以更高效地拷贝文件。 参见 [依赖于具体平台的高效拷贝操作](https://docs.python.org/zh-cn/3/library/shutil.html?highlight=copytree#shutil-platform-dependent-efficient-copy-operations) 一节。

*3.8 新版功能:* *dirs_exist_ok* 形参。