# C#与C++之间类型对照

> https://blog.csdn.net/JacksonH/article/details/436410

| **Windows Data Type**                                        | **.NET Data Type**           |
| ------------------------------------------------------------ | ---------------------------- |
| BOOL, BOOLEAN                                                | Boolean or Int32             |
| BSTR                                                         | String                       |
| BYTE                                                         | Byte                         |
| CHAR                                                         | Char                         |
| DOUBLE                                                       | Double                       |
| DWORD                                                        | Int32 or UInt32              |
| FLOAT                                                        | Single                       |
| HANDLE (and all other handle types, such as HFONT and HMENU) | IntPtr, UintPtr or HandleRef |
| HRESULT                                                      | Int32 or UInt32              |
| INT                                                          | Int32                        |
| LANGID                                                       | Int16 or UInt16              |
| LCID                                                         | Int32 or UInt32              |
| LONG                                                         | Int32                        |
| LPARAM                                                       | IntPtr, UintPtr or Object    |
| LPCSTR                                                       | String                       |
| LPCTSTR                                                      | String                       |
| LPCWSTR                                                      | String                       |
| LPSTR                                                        | String or StringBuilder*     |
| LPTSTR                                                       | String or StringBuilder      |
| LPWSTR                                                       | String or StringBuilder      |
| LPVOID                                                       | IntPtr, UintPtr or Object    |
| LRESULT                                                      | IntPtr                       |
| SAFEARRAY                                                    | .NET array type              |
| SHORT                                                        | Int16                        |
| TCHAR                                                        | Char                         |
| UCHAR                                                        | SByte                        |
| UINT                                                         | Int32 or UInt32              |
| ULONG                                                        | Int32 or UInt32              |
| VARIANT                                                      | Object                       |
| VARIANT_BOOL                                                 | Boolean                      |
| WCHAR                                                        | Char                         |
| WORD                                                         | Int16 or UInt16              |
| WPARAM                                                       | IntPtr, UintPtr or Object    |

注意；

- 在进行string转换时，需要加入前缀`[MarshalAs(UnmanagedType.LPStr)]`
- lpdword 对应于 ref int
- 在使用StringBuilder时你必须先给先分配空间也就是`StringBuilder className = new StringBuilder(255);`，DLL才会将结果存放到你申请的空间中。

> https://www.cnblogs.com/HappyEDay/p/5442909.html

| **C/C++**                                                    | **C#**                                |
| ------------------------------------------------------------ | ------------------------------------- |
| HANDLE, LPDWORD, LPVOID, void*                               | IntPtr                                |
| LPCTSTR, LPCTSTR, LPSTR, char*, const char*, Wchar_t*, LPWSTR | String [in], StringBuilder [in, out]  |
| DWORD, unsigned long, Ulong                                  | UInt32, [MarshalAs(UnmanagedType.U4)] |
| bool                                                         | bool                                  |
| LP<struct>                                                   | [In] ref <struct>                     |
| SIZE_T                                                       | uint                                  |
| LPDWORD                                                      | out uint                              |
| LPTSTR                                                       | [Out] StringBuilder                   |
| PULARGE_INTEGER                                              | out ulong                             |
| WORD                                                         | uInt16                                |
| Byte, unsigned char                                          | byte                                  |
| Short                                                        | Int16                                 |
| Long, int                                                    | Int32                                 |
| float                                                        | single                                |
| double                                                       | double                                |
| NULL pointer                                                 | IntPtr.Zero                           |
| Uint                                                         | Uint32                                |