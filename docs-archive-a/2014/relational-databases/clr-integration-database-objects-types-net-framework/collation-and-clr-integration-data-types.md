---
title: 照合順序と CLR 統合データ型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a5b0367487aeb80355b8c5c976818e1b6c1ac04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742286"
---
# <a name="collation-and-clr-integration-data-types"></a><span data-ttu-id="634ce-102">照合順序と CLR 統合データ型</span><span class="sxs-lookup"><span data-stu-id="634ce-102">Collation and CLR Integration Data Types</span></span>
  <span data-ttu-id="634ce-103">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] では、`CompareInfo` オブジェクトで照合順序が処理されます。</span><span class="sxs-lookup"><span data-stu-id="634ce-103">In the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], the `CompareInfo` object handles collations.</span></span> <span data-ttu-id="634ce-104">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の文字列 API (アプリケーション プログラミング インターフェイス) では、文字列比較を実行するために、現在のスレッドの `CompareInfo` オブジェクトに関連付けられた `CultureInfo` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="634ce-104">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] string application programming interfaces (APIs) use the `CompareInfo` property associated with the `CultureInfo` object of the current thread to perform string comparisons.</span></span> <span data-ttu-id="634ce-105">オブジェクトの既定の設定は、が実行されている `CultureInfo` [!INCLUDE[msCoName](../../includes/msconame-md.md)] コンピューターの Windows ロケール設定に基づいてい [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="634ce-105">The default setting of the `CultureInfo` object is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows locale setting for the computer on which [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span> <span data-ttu-id="634ce-106">`CultureInfo` 値の比較の既定の比較セマンティクスは、`System.String` が明示的に指定されていなければ、この設定で決定されます。</span><span class="sxs-lookup"><span data-stu-id="634ce-106">This determines the default comparison semantics, if no explicit `CultureInfo` is specified, for comparisons of `System.String` values.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="634ce-107">では、`CompareInfo` プロパティをデータベースまたはサーバーの照合順序に明示的に変更できせん。</span><span class="sxs-lookup"><span data-stu-id="634ce-107">does not explicitly change the `CompareInfo` property to the database or server collation.</span></span> <span data-ttu-id="634ce-108">必要であれば、適切な `CompareInfo` プロパティをユーザーがルーチン内で設定します。</span><span class="sxs-lookup"><span data-stu-id="634ce-108">If required, users must set the appropriate `CompareInfo` property in their routines.</span></span>  
  
## <a name="parameter-collation"></a><span data-ttu-id="634ce-109">パラメーターの照合順序</span><span class="sxs-lookup"><span data-stu-id="634ce-109">Parameter Collation</span></span>  
 <span data-ttu-id="634ce-110">CLR (共通言語ランタイム) ルーチンを作成するとき、そのルーチンにバインドされた CLR メソッドのパラメーターの型が `SQLString` の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、呼び出し元のルーチンを含むデータベースの既定の照合順序でパラメーターのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="634ce-110">When you create a common language runtime (CLR) routine, and a parameter of a CLR method bound to the routine is of type `SQLString`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creates an instance of the parameter with the default collation of the database containing the calling routine.</span></span> <span data-ttu-id="634ce-111">パラメーターが `SqlType` ではない場合 (たとえば、`String` ではなく `SQLString` の場合)、データベースからの照合順序情報はパラメーターに関連付けられません。</span><span class="sxs-lookup"><span data-stu-id="634ce-111">If a parameter is not a `SqlType` (for example, `String` rather than `SQLString`), the collation information from the database is not associated with the parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="634ce-112">参照</span><span class="sxs-lookup"><span data-stu-id="634ce-112">See Also</span></span>  
 [<span data-ttu-id="634ce-113">.NET Framework での SQL Server データ型</span><span class="sxs-lookup"><span data-stu-id="634ce-113">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
