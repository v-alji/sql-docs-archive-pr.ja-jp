---
title: '[すべてのプリンシパルを参照] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.browseprincipals.f1
ms.assetid: f11d2c5e-ee05-45f3-8dc2-0feb99b2f76f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c204411a4daace27745e46269cbcfa0ed33f323f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632643"
---
# <a name="browse-all-principals-dialog-box"></a><span data-ttu-id="86587-102">[すべてのプリンシパルを参照] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="86587-102">Browse All Principals Dialog Box</span></span>
  <span data-ttu-id="86587-103">**[すべてのプリンシパルを参照]** ダイアログ ボックスを使用して、データベースのプリンシパルを選択し、選択したプロジェクトに対する、または選択したフォルダーに格納されたすべてのプロジェクトに対するプリンシパルの権限を変更できます。</span><span class="sxs-lookup"><span data-stu-id="86587-103">Use the **Browse All Principals** dialog box to select a database principal to change the principal's permissions on the selected project or on all projects contained in a selected folder.</span></span>  
  
 <span data-ttu-id="86587-104">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="86587-104">**What do you want to do?**</span></span>  
  
-   <span data-ttu-id="86587-105">[[すべてのプリンシパルを参照] ダイアログ ボックスを開く](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="86587-105">[Open the Browse All Principals dialog box](#open_dialog)</span></span>  
  
-   [<span data-ttu-id="86587-106">オプションの構成</span><span class="sxs-lookup"><span data-stu-id="86587-106">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-browse-all-principals-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="86587-107">[すべてのプリンシパルを参照] ダイアログ ボックスを開く</span><span class="sxs-lookup"><span data-stu-id="86587-107">Open the Browse All Principals dialog box</span></span>  
  
1.  <span data-ttu-id="86587-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="86587-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="86587-109">SSISDB カタログをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続されます。</span><span class="sxs-lookup"><span data-stu-id="86587-109">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB catalog.</span></span>  
  
2.  <span data-ttu-id="86587-110">オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。</span><span class="sxs-lookup"><span data-stu-id="86587-110">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="86587-111">**[SSISDB]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="86587-111">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="86587-112">選択したフォルダーに格納されたすべてのプロジェクトに対するプリンシパルの権限を変更するには、フォルダーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="86587-112">To change the principal's permissions on all projects contained in a selected folder, right-click the folder and then click **Properties**.</span></span>  
  
     <span data-ttu-id="86587-113">選択したプロジェクトに対するプリンシパルの権限を変更するには、プロジェクトが格納されているフォルダーを展開し、プロジェクトを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="86587-113">To change the principal's permissions on a selected project, expand the folder that contains the project, right-click the project, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="86587-114">**[権限]** ページを選択し、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="86587-114">Select the **Permissions** page, and then click **Browse**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="86587-115">オプションの構成</span><span class="sxs-lookup"><span data-stu-id="86587-115">Configure the Options</span></span>  
 <span data-ttu-id="86587-116">このページには、SSISDB データベースのカタログ ビュー sys.database_principals から返されたプリンシパルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="86587-116">This page displays the principals from the catalog view, sys.database_principals, of the SSISDB database.</span></span>  
  
 <span data-ttu-id="86587-117">プリンシパルを選択した状態で、 **[OK]** をクリックして、 **[すべてのプリンシパルを参照]** ダイアログ ボックスを閉じると、そのプリンシパルが親ダイアログ ボックスの **[権限]** ページにある **[ログインまたはロール]** の一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="86587-117">Selecting principals adds them to the **Logins or roles** list on the **Permissions** page of the parent dialog box when you click **OK** and close the **Browse All Principals** dialog box.</span></span> <span data-ttu-id="86587-118">**[ログインまたはロール]** の一覧にプリンシパルを追加すると、そのプリンシパルの選択したプロジェクトに対する権限を変更できます。</span><span class="sxs-lookup"><span data-stu-id="86587-118">After adding principals to the **Logins or roles** list, you can change their permissions on the selected project.</span></span>  
  
 <span data-ttu-id="86587-119">**[選択列]**</span><span class="sxs-lookup"><span data-stu-id="86587-119">**Selection column**</span></span>  
 <span data-ttu-id="86587-120">親ダイアログ ボックスの **[権限]** ページにある **[ログインまたはロール]** の一覧にプリンシパルを追加する場合はオンにします。</span><span class="sxs-lookup"><span data-stu-id="86587-120">Select to add the principal to the **Logins or roles** list on the **Permissions** page of the parent dialog box.</span></span>  
  
 <span data-ttu-id="86587-121">**[アイコン列]**</span><span class="sxs-lookup"><span data-stu-id="86587-121">**Icon column**</span></span>  
 <span data-ttu-id="86587-122">プリンシパルの **[種類]** に対応したアイコンです。</span><span class="sxs-lookup"><span data-stu-id="86587-122">An icon that corresponds to the **Type** of the principal.</span></span>  
  
 <span data-ttu-id="86587-123">**Name**</span><span class="sxs-lookup"><span data-stu-id="86587-123">**Name**</span></span>  
 <span data-ttu-id="86587-124">プリンシパルの名前です。</span><span class="sxs-lookup"><span data-stu-id="86587-124">The name of the principal.</span></span>  
  
 <span data-ttu-id="86587-125">**Type**</span><span class="sxs-lookup"><span data-stu-id="86587-125">**Type**</span></span>  
 <span data-ttu-id="86587-126">プリンシパルの種類。</span><span class="sxs-lookup"><span data-stu-id="86587-126">The type of the principal.</span></span> <span data-ttu-id="86587-127">一般的な種類を次に示します。</span><span class="sxs-lookup"><span data-stu-id="86587-127">The common types are:</span></span>  
  
-   <span data-ttu-id="86587-128">SQL ユーザー</span><span class="sxs-lookup"><span data-stu-id="86587-128">SQL User</span></span>  
  
-   <span data-ttu-id="86587-129">Windows ユーザー</span><span class="sxs-lookup"><span data-stu-id="86587-129">Windows User</span></span>  
  
-   <span data-ttu-id="86587-130">データベース ロール</span><span class="sxs-lookup"><span data-stu-id="86587-130">Database Role</span></span>  
  
  
