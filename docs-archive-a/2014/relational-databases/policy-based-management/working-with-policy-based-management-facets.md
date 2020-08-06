---
title: ポリシー ベースの管理ファセットの操作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- viewing Policy-Based Management facets
- facets [Policy-Based Management], copying
- facets [Policy-Based Management], viewing
- copying Policy-Based Management facets
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5a356550796cc682b2292defffd6565b7fea0783
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634432"
---
# <a name="working-with-policy-based-management-facets"></a><span data-ttu-id="351f6-102">ポリシー ベースの管理ファセットの操作</span><span class="sxs-lookup"><span data-stu-id="351f6-102">Working with Policy-Based Management Facets</span></span>
  <span data-ttu-id="351f6-103">ポリシー ベースの管理ファセットは、管理対象の領域に関連する一連の論理プロパティです。</span><span class="sxs-lookup"><span data-stu-id="351f6-103">A Policy-Based Management facet is a set of logical properties that are related to an area of management interest.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="351f6-104">には、いくつかの定義済みファセットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="351f6-104">includes several predefined facets.</span></span> <span data-ttu-id="351f6-105">たとえば、セキュリティ構成ファセットは既定で無効になる機能をプロパティとして定義します。</span><span class="sxs-lookup"><span data-stu-id="351f6-105">For example, the Surface Area Configuration facet defines, as properties, the features that are off by default.</span></span>  
  
 <span data-ttu-id="351f6-106">同様の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境を多数管理する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の 1 つのインスタンスでファセットを構成し、ファセットの状態をファイルにコピーして、そのファイルを別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにポリシーとしてインポートできます。</span><span class="sxs-lookup"><span data-stu-id="351f6-106">When you manage many similar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environments, you can configure a facet in one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], copy the state of the facet to a file, and then import that file into another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a policy.</span></span> <span data-ttu-id="351f6-107">状態がポリシーに変換されたら、そのポリシーを別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス、インスタンス オブジェクト、データベース、またはデータベース オブジェクトに適用できます。</span><span class="sxs-lookup"><span data-stu-id="351f6-107">When the state has been converted to a policy, the policy can be applied to other instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], instance objects, databases, or database objects.</span></span>  
  
 <span data-ttu-id="351f6-108">このトピックでは、ファセットの状態を XML ファイルにコピーする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="351f6-108">This topic describes how to copy the state of a facet to an XML file.</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="351f6-109">Permissions</span><span class="sxs-lookup"><span data-stu-id="351f6-109">Permissions</span></span>  
 <span data-ttu-id="351f6-110">このトピックの手順では、msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="351f6-110">The procedures in this topic require membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
## <a name="viewing-and-copying-facet-states"></a><span data-ttu-id="351f6-111">ファセットの状態の表示とコピー</span><span class="sxs-lookup"><span data-stu-id="351f6-111">Viewing and Copying Facet States</span></span>  
 [<span data-ttu-id="351f6-112">SQL Server オブジェクトのポリシーベースの管理ファセットの表示</span><span class="sxs-lookup"><span data-stu-id="351f6-112">View the Policy-Based Management Facets on a SQL Server Object</span></span>](view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [<span data-ttu-id="351f6-113">XML ファイルへのポリシーベースの管理ファセットの状態のコピー</span><span class="sxs-lookup"><span data-stu-id="351f6-113">Copy a Policy-Based Management Facet State to an XML File</span></span>](copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## <a name="see-also"></a><span data-ttu-id="351f6-114">参照</span><span class="sxs-lookup"><span data-stu-id="351f6-114">See Also</span></span>  
 [<span data-ttu-id="351f6-115">ポリシー ベースの管理を使用したサーバーの管理</span><span class="sxs-lookup"><span data-stu-id="351f6-115">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
