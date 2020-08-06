---
title: XML ファイルへのポリシー ベースの管理ファセットの状態のコピー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7be2332d9a2507a079d85a3424bda3a387609ca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715198"
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a><span data-ttu-id="6c4fa-102">XML ファイルへのポリシー ベースの管理ファセットの状態のコピー</span><span class="sxs-lookup"><span data-stu-id="6c4fa-102">Copy a Policy-Based Management Facet State to an XML File</span></span>
  <span data-ttu-id="6c4fa-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシー ベースの管理ファセットの状態を XML ファイルにコピーする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6c4fa-103">This topic describes how to how to copy the state of a Policy-Based Management facet to an XML file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="6c4fa-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="6c4fa-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6c4fa-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="6c4fa-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6c4fa-106">Security</span><span class="sxs-lookup"><span data-stu-id="6c4fa-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6c4fa-107">**以下を使用してファセットの状態を XML ファイルにコピーするには:**</span><span class="sxs-lookup"><span data-stu-id="6c4fa-107">**To copy a facet state to an XML file, using:**</span></span>  
  
     [<span data-ttu-id="6c4fa-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6c4fa-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6c4fa-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="6c4fa-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6c4fa-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6c4fa-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6c4fa-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="6c4fa-111">Permissions</span></span>  
 <span data-ttu-id="6c4fa-112">このトピックの手順では、msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="6c4fa-112">The procedures in this topic require membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6c4fa-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="6c4fa-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a><span data-ttu-id="6c4fa-114">ファセットの状態を XML ファイルにコピーするには</span><span class="sxs-lookup"><span data-stu-id="6c4fa-114">To copy a facet state to an XML file</span></span>  
  
1.  <span data-ttu-id="6c4fa-115">オブジェクト エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス、インスタンス オブジェクト、データベース、またはデータベース オブジェクトを右クリックし、 **[ファセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c4fa-115">In Object Explorer, right-click an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], instance object, database, or database object, and then click **Facets**.</span></span>  
  
2.  <span data-ttu-id="6c4fa-116">**[ファセットを表示 -**_オブジェクト名_] ダイアログ ボックスで、**[現在の状態をポリシーとしてエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c4fa-116">In the **View Facets -**_object_name_ dialog box, click **Export Current State as Policy**.</span></span>  
  
3.  <span data-ttu-id="6c4fa-117">**[ポリシーとしてエクスポート]** ダイアログ ボックスで、ファイルのパスと名前を入力します。または、参照ボタン (**[...]**) を使用してファイルを指定し、XML ファイルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="6c4fa-117">In the **Export as Policy** dialog box, type the path and name of the file; or use the Browse (**...**) button to locate the file, and then type the name of the XML file.</span></span> <span data-ttu-id="6c4fa-118">このダイアログ ボックスで利用可能なオプションの詳細については、「 [Export As Policy Dialog Box](export-as-policy-dialog-box.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c4fa-118">For more information on the available options in this dialog box, see [Export As Policy Dialog Box](export-as-policy-dialog-box.md)</span></span>  
  
4.  <span data-ttu-id="6c4fa-119">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c4fa-119">When finished, click **OK**.</span></span>  
  
  
