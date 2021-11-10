#### OS.path - 操作文件

#### os.path.join(*path*, **paths*)

智能地拼接一个或多个路径部分。 返回值是 *path* 和 **paths* 的所有成员的拼接，其中每个非空部分后面都紧跟一个目录分隔符，最后一个部分除外，这意味着如果最后一个部分为空，则结果将以分隔符结尾。 如果某个部分为绝对路径，则之前的所有部分会被丢弃并从绝对路径部分开始继续拼接。

在 Windows 上，遇到绝对路径部分（例如 `r'\foo'`）时，不会重置盘符。如果某部分路径包含盘符，则会丢弃所有先前的部分，并重置盘符。请注意，由于每个驱动器都有一个“当前目录”，所以 `os.path.join("c:", "foo")` 表示驱动器 `C:` 上当前目录的相对路径 (`c:foo`)，而不是 `c:\foo`。

*在 3.6 版更改:* 接受一个 [类路径对象](https://docs.python.org/zh-cn/3/glossary.html#term-path-like-object) 用于 *path* 和 *paths* 。

#### os.path.isdir(path)

如果 *path* 是 [`现有的`](https://docs.python.org/zh-cn/3/library/os.path.html?highlight=os path join#os.path.exists) 目录，则返回 `True`。本方法会跟踪符号链接，因此，对于同一路径，[`islink()`](https://docs.python.org/zh-cn/3/library/os.path.html?highlight=os path join#os.path.islink) 和 [`isdir()`](https://docs.python.org/zh-cn/3/library/os.path.html?highlight=os path join#os.path.isdir) 都可能为 `True`。

*在 3.6 版更改:* 接受一个 [path-like object](https://docs.python.org/zh-cn/3/glossary.html#term-path-like-object)。

#### os.path.isfile(path)

如果 *path* 是 [`现有的`](https://docs.python.org/zh-cn/3/library/os.path.html?highlight=os path join#os.path.exists) 常规文件，则返回 `True`。本方法会跟踪符号链接，因此，对于同一路径，[`islink()`](https://docs.python.org/zh-cn/3/library/os.path.html?highlight=os path join#os.path.islink) 和 [`isfile()`](https://docs.python.org/zh-cn/3/library/os.path.html?highlight=os path join#os.path.isfile) 都可能为 `True`。

*在 3.6 版更改:* 接受一个 [path-like object](https://docs.python.org/zh-cn/3/glossary.html#term-path-like-object)。