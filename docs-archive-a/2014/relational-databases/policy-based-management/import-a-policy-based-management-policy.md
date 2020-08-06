---
title: ポリシー ベースの管理ポリシーのインポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, import policy
ms.assetid: 850b7ef9-d2b7-4754-bf04-7cb419ffb776
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d83ed589e147c61b1692447aacb17535f18a5c9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632438"
---
# <a name="import-a-policy-based-management-policy"></a><span data-ttu-id="357b6-102">ポリシー ベースの管理ポリシーのインポート</span><span class="sxs-lookup"><span data-stu-id="357b6-102">Import a Policy-Based Management Policy</span></span>
  <span data-ttu-id="357b6-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシー ベースの管理ポリシー インスタンスをインポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="357b6-103">This topic describes how to import a Policy-Based Management policy instance in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="357b6-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="357b6-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="357b6-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="357b6-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="357b6-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="357b6-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="357b6-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="357b6-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="357b6-108">**以下を使用してポリシー インスタンスをインポートするには:**</span><span class="sxs-lookup"><span data-stu-id="357b6-108">**To import a policy instance, using:**</span></span>  
  
     [<span data-ttu-id="357b6-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="357b6-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="357b6-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="357b6-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="357b6-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="357b6-111">Limitations and Restrictions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="357b6-112">には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの監視に使用できるポリシーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="357b6-112">ships with policies that can be used to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="357b6-113">これらのポリシーは、既定では[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]にインストールされませんが、既定の場所である C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033 からインポートできます。</span><span class="sxs-lookup"><span data-stu-id="357b6-113">By default, these policies are not installed on the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], but they can be imported from the default location of C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="357b6-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="357b6-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="357b6-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="357b6-115">Permissions</span></span>  
 <span data-ttu-id="357b6-116">msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="357b6-116">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="357b6-117">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="357b6-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-import-a-policy-instance"></a><span data-ttu-id="357b6-118">ポリシー インスタンスをインポートするには</span><span class="sxs-lookup"><span data-stu-id="357b6-118">To import a policy instance</span></span>  
  
1.  <span data-ttu-id="357b6-119">**オブジェクト エクスプローラー**で、プラス記号をクリックして、新しくインポートするポリシー インスタンスを配置するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="357b6-119">In **Object Explorer**, click the plus sign to expand the server where the newly-imported policy instance will reside.</span></span>  
  
2.  <span data-ttu-id="357b6-120">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="357b6-120">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="357b6-121">プラス記号をクリックして **[ポリシー管理]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="357b6-121">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="357b6-122">**[ポリシー]** フォルダーを右クリックし、 **[ポリシーのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="357b6-122">Right-click the **Policies** folder and select **Import Policy**.</span></span>  
  
5.  <span data-ttu-id="357b6-123">**[インポート]** ダイアログ ボックスで、ファイルのパスと名前を入力します。または、参照ボタン ( **[...]** ) を使用してポリシーを含んでいる XML ファイルを特定し、ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="357b6-123">In the **Import** dialog box, type the path and name of the file; or use the Browse (**...**) button to locate the XML file that contains the policy, and then select the file.</span></span> <span data-ttu-id="357b6-124">**[インポート]** ダイアログ ボックスで利用可能なオプションの詳細については、「 [Import Policies Dialog Box](import-policies-dialog-box.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="357b6-124">For more information on the available options in the **Import** dialog box, see [Import Policies Dialog Box](import-policies-dialog-box.md).</span></span>  
  
6.  <span data-ttu-id="357b6-125">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="357b6-125">When finished, click **OK**.</span></span>  
  
  
