---
title: 拡張ストアドプロシージャを SQL Server に追加する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], adding
- adding extended stored procedures
- collations [SQL Server], extended stored procedures
ms.assetid: 10f1bb74-3b43-4efd-b7ab-7a85a8600a50
author: rothja
ms.author: jroth
ms.openlocfilehash: 03ac8c2a0fa9ce77db59d50b3a7b9da42415e013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643360"
---
# <a name="adding-an-extended-stored-procedure-to-sql-server"></a><span data-ttu-id="d961b-102">SQL Server への拡張ストアド プロシージャの追加</span><span class="sxs-lookup"><span data-stu-id="d961b-102">Adding an Extended Stored Procedure to SQL Server</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="d961b-103">代わりに CLR Integration を使用してください。</span><span class="sxs-lookup"><span data-stu-id="d961b-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="d961b-104">拡張ストアド プロシージャ関数を含んでいる DLL は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の拡張機能としての役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="d961b-104">A DLL that contains extended stored procedure functions acts as an extension to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d961b-105">DLL をインストールするには、標準の dll ファイルが格納されているディレクトリ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (C:\Program Server\MSSQL12.0.\* ) にファイルをコピーします。x\*\MSSQL\Binn (既定)。</span><span class="sxs-lookup"><span data-stu-id="d961b-105">To install the DLL, copy the file to a directory, such as the one that contains the standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL files (C:\Program Files\Microsoft SQL Server\MSSQL12.0.*x*\MSSQL\Binn by default).</span></span>  
  
 <span data-ttu-id="d961b-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者は、拡張ストアド プロシージャ DLL をサーバーにコピーした後、DLL 内の各拡張ストアド プロシージャを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d961b-106">After the extended stored procedure DLL has been copied to the server, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator must register to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] each extended stored procedure function in the DLL.</span></span> <span data-ttu-id="d961b-107">この操作を行うには、sp_addextendedproc システム ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="d961b-107">This is done using the sp_addextendedproc system stored procedure.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d961b-108">システム管理者は、拡張ストアド プロシージャをサーバーに追加し、他のユーザーに実行権限を許可する前に、拡張ストアド プロシージャに有害なコードや悪意のあるコードが含まれていないことを十分に確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d961b-108">The system administrator should thoroughly review an extended stored procedure to ensure that it does not contain harmful or malicious code before adding it to the server and granting execute permissions to other users.</span></span>  <span data-ttu-id="d961b-109">すべてのユーザー入力を検証します。</span><span class="sxs-lookup"><span data-stu-id="d961b-109">Validate all user input.</span></span> <span data-ttu-id="d961b-110">また、ユーザー入力は検証するまで連結しないでください。</span><span class="sxs-lookup"><span data-stu-id="d961b-110">Do not concatenate user input before validating it.</span></span> <span data-ttu-id="d961b-111">検証していないユーザー入力から作成されたコマンドは、絶対に実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="d961b-111">Never execute a command constructed from unvalidated user input.</span></span>  
  
 <span data-ttu-id="d961b-112">sp_addextendedproc の最初のパラメーターには、関数の名前を指定します。2 番目のパラメーターには、その関数が含まれている DLL の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d961b-112">The first parameter of sp_addextendedproc specifies the name of the function, and the second parameter specifies the name of the DLL in which that function resides.</span></span> <span data-ttu-id="d961b-113">DLL の完全なパスを指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d961b-113">It is recommended that you specify the complete path of the DLL.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d961b-114">完全パスを使用して登録されなかった既存の DLL は、SQL Server 2005 以降へのアップグレード後に機能しなくなります。</span><span class="sxs-lookup"><span data-stu-id="d961b-114">Existing DLLs that were not registered with a complete path will not work after upgrading to SQL Server 2005 or later.</span></span> <span data-ttu-id="d961b-115">この問題を修正するには、sp_dropextendedproc を使用して DLL の登録を解除し、sp_addextendedproc を使用して完全パスと共に登録し直します。</span><span class="sxs-lookup"><span data-stu-id="d961b-115">To correct the problem, use sp_dropextendedproc to unregister the DLL, and then reregister it with sp_addextendedproc, specifying the complete path.</span></span>  
  
 <span data-ttu-id="d961b-116">`sp_addextendedproc` に指定する関数の名前は、大文字と小文字の区別を含め、DLL 内の関数名とまったく同じにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d961b-116">The name of the function specified in `sp_addextendedproc` must be exactly the same, including the case, as the function's name in the DLL.</span></span> <span data-ttu-id="d961b-117">たとえば、次のコマンドは `xp_hello,` という名前の dll に含まれている `xp_hello.dll` 関数を、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拡張ストアド プロシージャとして登録します。</span><span class="sxs-lookup"><span data-stu-id="d961b-117">For example, this command registers a function `xp_hello,` located in a dll named `xp_hello.dll`, as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] extended stored procedure:</span></span>  
  
```  
sp_addextendedproc 'xp_hello', 'c:\Program Files\Microsoft SQL Server\MSSQL12.0.MSSQLSERVER\MSSQL\Binn\xp_hello.dll';  
```  
  
 <span data-ttu-id="d961b-118">`sp_addextendedproc` に指定した関数の名前が、DLL 内の関数名と正確に一致しない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に新しい名前が登録されますが、その名前は役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="d961b-118">If the name of the function specified in `sp_addextendedproc` does not exactly match the function name in the DLL, the new name will be registered in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but the name will not be usable.</span></span> <span data-ttu-id="d961b-119">たとえば、 `xp_Hello` がに配置されている拡張ストアドプロシージャとして登録されていても、を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 関数を `xp_hello.dll` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `xp_Hello` 後で呼び出す場合、は DLL 内で関数を見つけることができません。</span><span class="sxs-lookup"><span data-stu-id="d961b-119">For example, although `xp_Hello` is registered as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] extended stored procedure located in `xp_hello.dll`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not be able to find the function in the DLL if you use `xp_Hello` to call the function later.</span></span>  
  
```  
--Register the function (xp_hello) with an initial upper case  
sp_addextendedproc 'xp_Hello', 'c:\xp_hello.dll';  
  
--Use the newly registered name to call the function  
DECLARE @txt varchar(33);  
EXEC xp_Hello @txt OUTPUT;  
  
--This is the error message  
Server: Msg 17750, Level 16, State 1, Procedure xp_Hello, Line 1  
Could not load the DLL xp_hello.dll, or one of the DLLs it references. Reason: 127(The specified procedure could not be found.).  
```  
  
 <span data-ttu-id="d961b-120">`sp_addextendedproc` に指定した関数の名前が DLL 内の関数名とまったく同じであり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの照合順序で大文字と小文字が区別されない場合、ユーザーは大文字と小文字を任意に組み合わせた名前を使用して、拡張ストアド プロシージャを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d961b-120">If the name of the function specified in `sp_addextendedproc` matches exactly the function name in the DLL, and the collation of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is case-insensitive, the user can call the extended stored procedure using any combination of lower- and upper-case letters of the name.</span></span>  
  
```  
--Register the function (xp_hello)  
sp_addextendedproc 'xp_hello', 'c:\xp_hello.dll';  
  
--The following will succeed in calling xp_hello  
DECLARE @txt varchar(33);  
EXEC xp_Hello @txt OUTPUT;  
  
DECLARE @txt varchar(33);  
EXEC xp_HelLO @txt OUTPUT;  
  
DECLARE @txt varchar(33);  
EXEC xp_HELLO @txt OUTPUT;  
```  
  
 <span data-ttu-id="d961b-121">名前と照合順序が DLL 内の関数とまったく同じになるように拡張ストアド プロシージャが登録されていても、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの照合順序で大文字と小文字が区別される場合は、呼び出し時に大文字と小文字を誤ると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はこの拡張ストアド プロシージャを呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="d961b-121">When the collation of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is case-sensitive, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not be able to call the extended stored procedure -- even if it was registered with exactly the same name and collation as the function in the DLL -- if the procedure is called with a different case.</span></span>  
  
```  
--Register the function (xp_hello)  
sp_addextendedproc 'xp_hello', 'c:\xp_hello.dll';  
  
--The following will result in an error  
DECLARE @txt varchar(33);  
EXEC xp_HELLO @txt OUTPUT;  
  
--This is the error  
Server: Msg 2812, Level 16, State 62, Line 1  
```  
  
 <span data-ttu-id="d961b-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を停止して再起動する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d961b-122">It is not necessary to stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d961b-123">参照</span><span class="sxs-lookup"><span data-stu-id="d961b-123">See Also</span></span>  
 <span data-ttu-id="d961b-124">[sp_addextendedproc &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d961b-124">[sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span></span>  
 [<span data-ttu-id="d961b-125">sp_dropextendedproc &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d961b-125">sp_dropextendedproc &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
