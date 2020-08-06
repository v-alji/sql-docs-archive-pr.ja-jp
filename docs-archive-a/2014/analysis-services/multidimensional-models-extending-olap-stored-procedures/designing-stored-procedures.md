---
title: ストアドプロシージャの設計 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 42b33873d6bdf28f7f702bcf186d681f57d6024d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715841"
---
# <a name="designing-stored-procedures"></a><span data-ttu-id="435ce-102">ストアド プロシージャのデザイン</span><span class="sxs-lookup"><span data-stu-id="435ce-102">Designing Stored Procedures</span></span>
  <span data-ttu-id="435ce-103">ストアド プロシージャでは、管理オブジェクト モデルである分析管理オブジェクト (AMO) とクライアント指向のオブジェクト モデルである [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX&#xAE; Data Objects (Multidimensional) (ADO MD) の両方を使用できます。</span><span class="sxs-lookup"><span data-stu-id="435ce-103">Both the administrative object model Analysis Management Objects (AMO) and the client oriented object model [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® Data Objects (Multidimensional) (ADO MD) are available in stored procedures.</span></span>  
  
 <span data-ttu-id="435ce-104">ストアド プロシージャを呼び出すには、多次元式 (MDX) レベルで表示できるスコープ内 (サーバーまたはデータベース) に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="435ce-104">Stored procedures must be in scope (either the server or the database) to be visible at the Multidimensional Expressions (MDX) level to be called.</span></span> <span data-ttu-id="435ce-105">ただし、ストアド プロシージャを呼び出した後、そのスコープがその親のアクションに制限されることはありません。</span><span class="sxs-lookup"><span data-stu-id="435ce-105">However, once a stored procedure is invoked, its scope is not limited to actions under its parent.</span></span> <span data-ttu-id="435ce-106">ストアド プロシージャは、サーバー上のどこでも変更を行うことができ、そのストアド プロシージャを呼び出すユーザー プロセスのセキュリティ制限と、そのストアド プロシージャが実行されるトランザクションの制限のみを受けます。</span><span class="sxs-lookup"><span data-stu-id="435ce-106">A stored procedure may make changes or modifications anywhere on the server, subject only to the security limitations of the user process that invokes it or to the limitations of the transaction in which it is operating.</span></span>  
  
 <span data-ttu-id="435ce-107">サーバー スコープ プロシージャは、サーバー上のすべてのコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="435ce-107">Server scope procedures are available in all contexts on the server.</span></span> <span data-ttu-id="435ce-108">データベース スコープ ストアド プロシージャは、そのプロシージャが定義されているデータベースのデータベース コンテキストのみで表示されます。</span><span class="sxs-lookup"><span data-stu-id="435ce-108">Database scope stored procedures are visible only in the database context of the database in which they are defined.</span></span>  
  
 <span data-ttu-id="435ce-109">他のすべての MDX 関数と同様に、ストアド プロシージャは MDX セッションを続行する前に解決する必要があります。ストアド プロシージャでは、実行中に MDX セッションがロックされるためです。</span><span class="sxs-lookup"><span data-stu-id="435ce-109">As with any MDX function, stored procedure must be resolved before an MDX session can continue; stored procedures lock MDX sessions while executing.</span></span> <span data-ttu-id="435ce-110">ユーザーの操作があるまで MDX セッションを一時停止しておく特別な理由がある場合を除き、ユーザーの操作 (ダイアログ ボックスなど) は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="435ce-110">Unless a specific reason exists to halt an MDX session pending user interaction, then user interactions (such as dialog boxes) are discouraged.</span></span>  
  
## <a name="dependent-assemblies"></a><span data-ttu-id="435ce-111">依存アセンブリ</span><span class="sxs-lookup"><span data-stu-id="435ce-111">Dependent Assemblies</span></span>  
 <span data-ttu-id="435ce-112">共通言語ランタイム (CLR) で検索できるようにするには、すべての依存アセンブリを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに読み込む必要があります</span><span class="sxs-lookup"><span data-stu-id="435ce-112">All dependent assemblies must be loaded into an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to be found by the common language runtime (CLR).</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="435ce-113">ではメイン アセンブリと同じフォルダーに依存アセンブリが保存されるので、そのようなアセンブリ内の関数に対するすべての関数参照は CLR によって自動的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="435ce-113">stores the dependent assemblies in the same folder as the main assembly, so the CLR automatically resolves all function references to functions in those assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="435ce-114">参照</span><span class="sxs-lookup"><span data-stu-id="435ce-114">See Also</span></span>  
 <span data-ttu-id="435ce-115">[多次元モデルのアセンブリの管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="435ce-115">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="435ce-116">ストアドプロシージャの定義</span><span class="sxs-lookup"><span data-stu-id="435ce-116">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
