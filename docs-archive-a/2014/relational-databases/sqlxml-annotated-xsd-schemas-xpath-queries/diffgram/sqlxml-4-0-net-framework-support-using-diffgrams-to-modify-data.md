---
title: データを変更するための Diffgram の使用 4.0 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- data deletions [SQLXML]
- updating data [SQLXML]
- DiffGrams [SQLXML]
- modifying data [SQLXML]
- .NET Framework [SQLXML], DiffGrams
- XML [SQLXML]
- database modifications [SQLXML]
- data updates [SQLXML]
- data modifications [SQLXML]
- record insertion [SQLXML]
- SQLXML, DiffGrams
- deleting data
- record updates [SQLXML]
- record deletions [SQLXML]
ms.assetid: 48b8a8f9-f3af-404f-8c84-f4c3703364d9
author: rothja
ms.author: jroth
ms.openlocfilehash: cc2e24304679a7648f18148eb45f33b9bf719a9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641550"
---
# <a name="using-diffgrams-to-modify-data-in-sqlxml-40"></a><span data-ttu-id="7eb34-102">SQLXML 4.0 での、DiffGram を使用したデータ変更</span><span class="sxs-lookup"><span data-stu-id="7eb34-102">Using DiffGrams to Modify Data in SQLXML 4.0</span></span>
  <span data-ttu-id="7eb34-103">DiffGram 形式は、.NET Framework の**データセット**コンポーネントで導入されました [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7eb34-103">The DiffGram format is introduced in the **DataSet** component of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="7eb34-104">.NET Framework では、DiffGram を作成して、Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースのテーブルのデータを変更するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="7eb34-104">Within the .NET Framework, you can create DiffGrams and use them to modify data in tables in a Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7eb34-105">ここでは、DiffGram の概要について説明し、使用例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="7eb34-105">This section provides a brief introduction to DiffGrams and examples of how to use them.</span></span> <span data-ttu-id="7eb34-106">.NET Framework での DiffGram の機能について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="7eb34-106">It is assumed that you are familiar with DiffGrams in the .NET Framework.</span></span> <span data-ttu-id="7eb34-107">このドキュメントでは、SQLXML に固有の DiffGram に関する問題を中心に説明します。</span><span class="sxs-lookup"><span data-stu-id="7eb34-107">In this documentation, the primary focus is on DiffGram issues that are specific to SQLXML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7eb34-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7eb34-108">In This Section</span></span>  
 [<span data-ttu-id="7eb34-109">SQLXML 4.0 の DiffGram の概要</span><span class="sxs-lookup"><span data-stu-id="7eb34-109">Introduction to DiffGrams in SQLXML 4.0</span></span>](introduction-to-diffgrams-in-sqlxml-4-0.md)  
 <span data-ttu-id="7eb34-110">DiffGram についての基本的な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="7eb34-110">Provides basic information about Diffgrams.</span></span>  
  
 [<span data-ttu-id="7eb34-111">&#40;SQLXML 4.0&#41;の DiffGram の例</span><span class="sxs-lookup"><span data-stu-id="7eb34-111">DiffGram Examples &#40;SQLXML 4.0&#41;</span></span>](diffgram-examples-sqlxml-4-0.md)  
 <span data-ttu-id="7eb34-112">DiffGram の使用例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="7eb34-112">Provides examples of using Diffgrams.</span></span>  
  
 [<span data-ttu-id="7eb34-113">ADO を使用した DiffGram の実行 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="7eb34-113">Executing a DiffGram by Using ADO &#40;SQLXML 4.0&#41;</span></span>](executing-a-diffgram-by-using-ado-sqlxml-4-0.md)  
 <span data-ttu-id="7eb34-114">ADO (ActiveX Data Objects) での DiffGram の実行例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="7eb34-114">Provides an example of executing a Diffgram with ActiveX Data Objects (ADO).</span></span>  
  
 [<span data-ttu-id="7eb34-115">SQLXML マネージド クラスを使用した、DiffGram の実行</span><span class="sxs-lookup"><span data-stu-id="7eb34-115">Executing a DiffGram by Using SQLXML Managed Classes</span></span>](../net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)  
 <span data-ttu-id="7eb34-116">SQLXML マネージド クラスでの DiffGram の実行例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="7eb34-116">Provides an example of executing a Diffgram with SQLXML Managed Classes.</span></span>  
  
  
