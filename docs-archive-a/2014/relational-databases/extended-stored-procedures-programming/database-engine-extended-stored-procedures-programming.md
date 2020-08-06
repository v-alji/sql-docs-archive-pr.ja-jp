---
title: 拡張ストアドプロシージャのプログラミング |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- gateway applications [SQL Server]
- extended stored procedures [SQL Server], about extended stored procedures
- Open Data Services [SQL Server]
- ODS [SQL Server]
ms.assetid: 561305cd-c803-48af-9eec-2c19f4d311ce
author: rothja
ms.author: jroth
ms.openlocfilehash: 30792cc2b431e35a8f7df5ff7bbb2c228892d5c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643359"
---
# <a name="programming-extended-stored-procedures"></a><span data-ttu-id="ecbe6-102">拡張ストアド プロシージャのプログラミング</span><span class="sxs-lookup"><span data-stu-id="ecbe6-102">Programming Extended Stored Procedures</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="ecbe6-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="ecbe6-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="ecbe6-104">以前は、SQL Server 以外のデータベース環境とのゲートウェイなど、サーバー アプリケーションの記述には Open Data Services が使用されていましたが、</span><span class="sxs-lookup"><span data-stu-id="ecbe6-104">In the past, Open Data Services was used to write server applications, such as gateways to non-SQL Server database environments.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="ecbe6-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、Open DATA SERVICES API の古い部分はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ecbe6-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not support the obsolete portions of the Open Data Services API.</span></span> <span data-ttu-id="ecbe6-106">当初の Open Data Services API のうち、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で現在でもサポートされているのは拡張ストアド プロシージャ関数の部分のみです。このため、Open Data Services API は拡張ストアド プロシージャ API という名前に変わりました。</span><span class="sxs-lookup"><span data-stu-id="ecbe6-106">The only part of the original Open Data Services API still supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are the extended stored procedure functions, so the API has been renamed to the Extended Stored Procedure API.</span></span>  
  
 <span data-ttu-id="ecbe6-107">拡張ストアド プロシージャ API アプリケーションへのニーズは、現在では分散クエリや CLR 統合などの強力な新しいテクノロジにほとんど移行しています。</span><span class="sxs-lookup"><span data-stu-id="ecbe6-107">With the emergence of newer and more powerful technologies, such as distributed queries and CLR Integration, the need for Extended Stored Procedure API applications has largely been replaced.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ecbe6-108">既存のゲートウェイ アプリケーションがある場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に付属している opends60.dll を使用してアプリケーションを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="ecbe6-108">If you have existing gateway applications, you cannot use the opends60.dll that ships with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to run the applications.</span></span> <span data-ttu-id="ecbe6-109">ゲートウェイ アプリケーションはサポート対象外になりました。</span><span class="sxs-lookup"><span data-stu-id="ecbe6-109">Gateway applications are no longer supported.</span></span>  
  
## <a name="extended-stored-procedures-vs-clr-integration"></a><span data-ttu-id="ecbe6-110">拡張ストアド プロシージャと CLR 統合</span><span class="sxs-lookup"><span data-stu-id="ecbe6-110">Extended Stored Procedures vs. CLR Integration</span></span>  
 <span data-ttu-id="ecbe6-111">以前のリリースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、[!INCLUDE[tsql](../../includes/tsql-md.md)] で表現することが非常に困難であるか記述が不可能なサーバー側ロジックをデータベース アプリケーション開発者が記述するための唯一の方法として、XP (拡張ストアド プロシージャ) が用意されていました。</span><span class="sxs-lookup"><span data-stu-id="ecbe6-111">In earlier releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], extended stored procedures (XPs) provided the only mechanism that was available for database application developers to write server-side logic that was either hard to express or impossible to write in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ecbe6-112">CLR 統合は、このような拡張ストアド プロシージャの記述に代わる、より堅牢な手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="ecbe6-112">CLR Integration provides a more robust alternative to writing such stored procedures.</span></span> <span data-ttu-id="ecbe6-113">さらに、CLR 統合を使用すると、ストアド プロシージャの形式で記述していたロジックが、テーブル値関数でさらに的確に表現できる場合が多くあります。これにより、関数が生成する結果を SELECT ステートメントの FROM 句に埋め込んでクエリできるようになります。</span><span class="sxs-lookup"><span data-stu-id="ecbe6-113">Furthermore, with CLR Integration, logic that used to be written in the form of stored procedures is often better expressed as table-valued functions, which allow the results constructed by the function to be queried in SELECT statements by embedding them in the FROM clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecbe6-114">参照</span><span class="sxs-lookup"><span data-stu-id="ecbe6-114">See Also</span></span>  
 <span data-ttu-id="ecbe6-115">[CLR&#41; 統合の概要 &#40;共通言語ランタイム](../clr-integration/common-language-runtime-integration-overview.md) </span><span class="sxs-lookup"><span data-stu-id="ecbe6-115">[Common Language Runtime &#40;CLR&#41; Integration Overview](../clr-integration/common-language-runtime-integration-overview.md) </span></span>  
 [<span data-ttu-id="ecbe6-116">CLR テーブル値関数</span><span class="sxs-lookup"><span data-stu-id="ecbe6-116">CLR Table-Valued Functions</span></span>](../clr-integration-database-objects-user-defined-functions/clr-table-valued-functions.md)  
  
  
