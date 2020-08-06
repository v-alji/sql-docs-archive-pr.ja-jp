---
title: 拡張ストアドプロシージャの作成 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- warnings [SQL Server]
- extended stored procedures [SQL Server], debugging
- extended stored procedures [SQL Server], creating
- messages [SQL Server], extended stored procedures
ms.assetid: 9f7c0cdb-6d88-44c0-b049-29953ae75717
author: rothja
ms.author: jroth
ms.openlocfilehash: d243b27b8542ec5fe10d795de1729d6c1fe484c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643358"
---
# <a name="creating-extended-stored-procedures"></a><span data-ttu-id="d84a4-102">拡張ストアド プロシージャの作成</span><span class="sxs-lookup"><span data-stu-id="d84a4-102">Creating Extended Stored Procedures</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="d84a4-103">代わりに CLR Integration を使用してください。</span><span class="sxs-lookup"><span data-stu-id="d84a4-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="d84a4-104">拡張ストアド プロシージャは、次に示すプロトタイプを備えた関数です。</span><span class="sxs-lookup"><span data-stu-id="d84a4-104">An extended stored procedure is a function with a prototype:</span></span>  
  
 <span data-ttu-id="d84a4-105">SRVRETCODE *xp_extendedProcName* **(** SRVPROC **\*);**</span><span class="sxs-lookup"><span data-stu-id="d84a4-105">SRVRETCODE *xp_extendedProcName* **(** SRVPROC **\*);**</span></span>  
  
 <span data-ttu-id="d84a4-106">プレフィックス xp_ は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d84a4-106">Using the prefix xp_ is optional.</span></span> <span data-ttu-id="d84a4-107">拡張ストアド プロシージャ名は、サーバーにインストールされたコード ページや並べ替え順に関係なく、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでの参照時には常に大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="d84a4-107">Extended stored procedure names are case sensitive when referenced in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, regardless of code page/sort order installed on the server.</span></span> <span data-ttu-id="d84a4-108">DLL を作成する際は、次の点に注意します。</span><span class="sxs-lookup"><span data-stu-id="d84a4-108">When you build a DLL:</span></span>  
  
-   <span data-ttu-id="d84a4-109">エントリ ポイントが必要である場合は、DllMain 関数を記述します。</span><span class="sxs-lookup"><span data-stu-id="d84a4-109">If an entry point is necessary, write a DllMain function.</span></span>  
  
     <span data-ttu-id="d84a4-110">この関数は省略可能です。ソース コードに記述されていない場合は、コンパイラにより独自のバージョン (何も実行せずに TRUE を返す) がリンクされます。</span><span class="sxs-lookup"><span data-stu-id="d84a4-110">This function is optional; if you do not provide it in source code, the compiler links its own version, which does nothing but return TRUE.</span></span> <span data-ttu-id="d84a4-111">DllMain 関数を記述した場合は、スレッドまたは処理が DLL にアタッチされる際、または DLL からデタッチされる際に、オペレーティング システムによってこの関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d84a4-111">If you provide a DllMain function, the operating system calls this function when a thread or process attaches to or detaches from the DLL.</span></span>  
  
-   <span data-ttu-id="d84a4-112">DLL 外部から呼び出す関数 (拡張ストアド プロシージャ関数) はすべて、エクスポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d84a4-112">All functions called from outside the DLL (all extended stored procedure Efunctions) must be exported.</span></span>  
  
     <span data-ttu-id="d84a4-113">関数をエクスポートするには、.def ファイルの [エクスポート] セクションで名前を指定します。または、ソースコード内の関数名の前に、Microsoft コンパイラ拡張機能 ( \_ _declspec () が2つのアンダースコアで始まることに注意してください) を __declspec します。</span><span class="sxs-lookup"><span data-stu-id="d84a4-113">You can export a function by listing its name in the EXPORTS section of a .def file, or you can prefix the function name in the source code with __declspec(dllexport), a Microsoft compiler extension (Note that \__declspec() begins with two underscores).</span></span>  
  
 <span data-ttu-id="d84a4-114">拡張ストアド プロシージャ DLL を作成するには、次のファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="d84a4-114">These files are required for creating an extended stored procedure DLL.</span></span>  
  
|<span data-ttu-id="d84a4-115">ファイル</span><span class="sxs-lookup"><span data-stu-id="d84a4-115">File</span></span>|<span data-ttu-id="d84a4-116">説明</span><span class="sxs-lookup"><span data-stu-id="d84a4-116">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="d84a4-117">Srv.h</span><span class="sxs-lookup"><span data-stu-id="d84a4-117">Srv.h</span></span>|<span data-ttu-id="d84a4-118">拡張ストアド プロシージャ API ヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="d84a4-118">Extended Stored Procedure API header file</span></span>|  
|<span data-ttu-id="d84a4-119">Opends60.lib</span><span class="sxs-lookup"><span data-stu-id="d84a4-119">Opends60.lib</span></span>|<span data-ttu-id="d84a4-120">Opends60.dll のインポート ライブラリ</span><span class="sxs-lookup"><span data-stu-id="d84a4-120">Import library for Opends60.dll</span></span>|  
  
 <span data-ttu-id="d84a4-121">拡張ストアド プロシージャ DLL を作成するには、ダイナミック リンク ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d84a4-121">To create an extended stored procedure DLL, create a project of type Dynamic Link Library.</span></span> <span data-ttu-id="d84a4-122">DLL の作成に関する詳細については、開発環境のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d84a4-122">For more information about creating a DLL, see the development environment documentation.</span></span>  
  
 <span data-ttu-id="d84a4-123">すべての拡張ストアド プロシージャ DLL で次の関数を実装およびエクスポートすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d84a4-123">It is highly recommended that all extended stored procedure DLLs implement and export the following function:</span></span>  
  
```  
__declspec(dllexport) ULONG __GetXpVersion()  
{  
   return ODS_VERSION;  
}  
```  
  
> [!NOTE]  
>  <span data-ttu-id="d84a4-124">__declspec(dllexport) は Microsoft 固有のコンパイラ拡張子です。</span><span class="sxs-lookup"><span data-stu-id="d84a4-124">__declspec(dllexport) is a Microsoft-specific compiler extension.</span></span> <span data-ttu-id="d84a4-125">お使いのコンパイラでこのディレクティブがサポートされない場合は、DEF ファイルの EXPORTS セクションでこの関数をエクスポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d84a4-125">If your compiler does not support this directive, you should export this function in your DEF file under the EXPORTS section.</span></span>  
  
 <span data-ttu-id="d84a4-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がトレースフラグ-T260 を使用して起動された場合、またはシステム管理者特権を持つユーザーが DBCC TRACEON (260) を実行していて、拡張ストアドプロシージャ dll で __GetXpVersion () がサポートされていない場合、警告メッセージ (エラー 8131: 拡張ストアドプロシージャ dll '% ' はエクスポート \_ _GetXpVersion ()) がエラーログに出力され</span><span class="sxs-lookup"><span data-stu-id="d84a4-126">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started with the trace flag -T260 or if a user with system administrator privileges runs DBCC TRACEON (260), and if the extended stored procedure DLL does not support __GetXpVersion(), a warning message (Error 8131: Extended stored procedure DLL '%' does not export \__GetXpVersion().) is printed to the error log.</span></span> <span data-ttu-id="d84a4-127">( \_ _GetXpVersion () は、2つのアンダースコアで始まります)。</span><span class="sxs-lookup"><span data-stu-id="d84a4-127">(Note that \__GetXpVersion() begins with two underscores.)</span></span>  
  
 <span data-ttu-id="d84a4-128">拡張ストアド プロシージャ DLL により __GetXpVersion() がエクスポートされ、この関数によって返されるバージョンがサーバーで要求されるバージョンよりも低い場合、この関数によって返されたバージョンとサーバーが必要とするバージョンを示す警告メッセージがエラー ログに出力されます。</span><span class="sxs-lookup"><span data-stu-id="d84a4-128">If the extended stored procedure DLL exports __GetXpVersion(), but the version returned by the function is less than that required by the server, a warning message stating the version returned by the function and the version expected by the server is printed to the error log.</span></span> <span data-ttu-id="d84a4-129">このメッセージが表示された場合は、_GetXpVersion () から正しくない値が返され \_ ているか、以前のバージョンの srv.sys を使用してコンパイルしています。</span><span class="sxs-lookup"><span data-stu-id="d84a4-129">If you get this message, you are returning an incorrect value from \__GetXpVersion(), or you are compiling with an older version of srv.h.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d84a4-130">拡張ストアド プロシージャでは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 関数 SetErrorMode を呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="d84a4-130">SetErrorMode, a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 function, should not be called in extended stored procedures.</span></span>  
  
 <span data-ttu-id="d84a4-131">実行時間の長い拡張ストアド プロシージャの場合は、srv_got_attention を定期的に呼び出すことにより、接続が強制的に切断された場合やバッチが中断された場合に、その拡張ストアド プロシージャが自身を終了できるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d84a4-131">It is recommended that a long-running extended stored procedure should call srv_got_attention periodically so that the procedure can terminate itself if the connection is killed or the batch is aborted.</span></span>  
  
 <span data-ttu-id="d84a4-132">拡張ストアド プロシージャ DLL をデバッグするには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Binn ディレクトリにその拡張ストアド プロシージャをコピーします。</span><span class="sxs-lookup"><span data-stu-id="d84a4-132">To debug an extended stored procedure DLL, copy it to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Binn directory.</span></span> <span data-ttu-id="d84a4-133">デバッグセッションの実行可能ファイルを指定するには、実行可能ファイルのパスとファイル名を入力し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます (たとえば、C:\PROGRAM の SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe)。</span><span class="sxs-lookup"><span data-stu-id="d84a4-133">To specify the executable for the debugging session, enter the path and file name of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executable file (for example, C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe).</span></span> <span data-ttu-id="d84a4-134">Sqlservr.exe 引数の詳細については、「 [Sqlservr.exe アプリケーション](../../tools/sqlservr-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d84a4-134">For information about sqlservr arguments, see [sqlservr Application](../../tools/sqlservr-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d84a4-135">参照</span><span class="sxs-lookup"><span data-stu-id="d84a4-135">See Also</span></span>  
 [<span data-ttu-id="d84a4-136">srv_got_attention &#40;拡張ストアドプロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="d84a4-136">srv_got_attention &#40;Extended Stored Procedure API&#41;</span></span>](../extended-stored-procedures-reference/srv-got-attention-extended-stored-procedure-api.md)  
  
  
