---
title: Try. を使用しています。ネイティブコンパイルストアドプロシージャでのキャッチ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f730e70c-4f92-411d-9984-289e241e43ee
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2d1f13a8fab6293eedc77a7ce93d86618a33d8c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715681"
---
# <a name="using-trycatch-in-natively-compiled-stored-procedures"></a><span data-ttu-id="903b8-102">ネイティブ コンパイル ストアド プロシージャでの Try..Catch の使用</span><span class="sxs-lookup"><span data-stu-id="903b8-102">Using Try..Catch in Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="903b8-103">ネイティブ コンパイル ストアド プロシージャ内で try..catch ブロックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="903b8-103">You can use try..catch blocks inside a natively compiled stored procedure.</span></span> <span data-ttu-id="903b8-104">次の構造がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="903b8-104">The following constructs are supported:</span></span>  
  
-   <span data-ttu-id="903b8-105">ERROR_LINE</span><span class="sxs-lookup"><span data-stu-id="903b8-105">ERROR_LINE</span></span>  
  
-   <span data-ttu-id="903b8-106">ERROR_MESSAGE</span><span class="sxs-lookup"><span data-stu-id="903b8-106">ERROR_MESSAGE</span></span>  
  
-   <span data-ttu-id="903b8-107">ERROR_NUMBER</span><span class="sxs-lookup"><span data-stu-id="903b8-107">ERROR_NUMBER</span></span>  
  
-   <span data-ttu-id="903b8-108">ERROR_PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="903b8-108">ERROR_PROCEDURE</span></span>  
  
-   <span data-ttu-id="903b8-109">ERROR_SEVERITY</span><span class="sxs-lookup"><span data-stu-id="903b8-109">ERROR_SEVERITY</span></span>  
  
-   <span data-ttu-id="903b8-110">ERROR_STATE</span><span class="sxs-lookup"><span data-stu-id="903b8-110">ERROR_STATE</span></span>  
  
```sql  
CREATE PROCEDURE test_try_catch  
with native_compilation, schemabinding, execute as owner   
as  
begin atomic with (transaction isolation level = snapshot, language = N'us_english')  
  
  BEGIN TRY  
    -- generate error  
    declare @i int = 1,  
    @j int = 0  
    select @i/@j  
  END TRY  
  BEGIN CATCH  
    -- Execute error retrieval routine.  
    SELECT  
    ERROR_SEVERITY() AS ErrorSeverity  
    ,ERROR_STATE() AS ErrorState  
    ,ERROR_PROCEDURE() AS ErrorProcedure  
    ,ERROR_LINE() AS ErrorLine  
    ,ERROR_MESSAGE() AS ErrorMessage  
  END CATCH  
end  
go  
  
exec test_try_catch  
go  
```  
  
## <a name="see-also"></a><span data-ttu-id="903b8-111">参照</span><span class="sxs-lookup"><span data-stu-id="903b8-111">See Also</span></span>  
 [<span data-ttu-id="903b8-112">ネイティブ コンパイル ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="903b8-112">Natively Compiled Stored Procedures</span></span>](../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
