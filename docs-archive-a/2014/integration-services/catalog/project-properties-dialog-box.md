---
title: '[プロジェクトのプロパティ] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isprojectprop.general.f1
- sql12.ssis.ssms.isprojectprop.permissions.f1
ms.assetid: d5cf52f5-1fe2-438a-98a3-fe117360acf8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 259ad48f2b1f33356243635bbaa5426a5199eccf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715649"
---
# <a name="project-properties-dialog-box"></a><span data-ttu-id="cf3b3-102">[プロジェクトのプロパティ] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="cf3b3-102">Project Properties Dialog Box</span></span>
  <span data-ttu-id="cf3b3-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトは、配置の 1 単位です。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-103">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project is a unit of deployment.</span></span> <span data-ttu-id="cf3b3-104">各プロジェクトには、パッケージ、パラメーター、および環境の参照を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-104">Each project can contain packages, parameters, and environment references.</span></span> <span data-ttu-id="cf3b3-105">プロジェクトはセキュリティ保護可能なオブジェクトであり、データベース プリンシパルの権限を定義できます。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-105">A project is a securable object and can define permissions for database principals.</span></span> <span data-ttu-id="cf3b3-106">プロジェクトを再配置するときに、以前のバージョンのプロジェクトを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログに保存できます。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-106">When a project is re-deployed, the previous version of the project can be stored in the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalog.</span></span>  
  
 <span data-ttu-id="cf3b3-107">プロジェクト パラメーターとパッケージ パラメーターを使用して、実行時にパッケージ内のプロパティに値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-107">Project parameters and package parameters can be used to assign values to properties within packages at the time of execution.</span></span> <span data-ttu-id="cf3b3-108">パッケージを実行する前に値が必要なパラメーターもあります。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-108">Some parameters require values before the package can be executed.</span></span> <span data-ttu-id="cf3b3-109">環境変数を参照するパラメーター値がある場合は、実行する前に、プロジェクトに対応する環境の参照を含めておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-109">Parameter values that reference environment variables require that the project has the corresponding environment reference prior to execution.</span></span>  
  
 <span data-ttu-id="cf3b3-110">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="cf3b3-110">**What do you want to do?**</span></span>  
  
-   <span data-ttu-id="cf3b3-111">[[プロジェクトのプロパティ] ダイアログ ボックスを開く](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="cf3b3-111">[Open the Project Properties dialog box](#open_dialog)</span></span>  
  
-   <span data-ttu-id="cf3b3-112">[[全般] ページのオプションの設定](#general)</span><span class="sxs-lookup"><span data-stu-id="cf3b3-112">[Set the options on the General page](#general)</span></span>  
  
-   <span data-ttu-id="cf3b3-113">[[権限] ページのオプションの設定](#permissions)</span><span class="sxs-lookup"><span data-stu-id="cf3b3-113">[Set the options on the Permissions page](#permissions)</span></span>  
  
##  <a name="open-the-project-properties-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="cf3b3-114">[プロジェクトのプロパティ] ダイアログ ボックスを開く</span><span class="sxs-lookup"><span data-stu-id="cf3b3-114">Open the Project Properties dialog box</span></span>  
  
1.  <span data-ttu-id="cf3b3-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="cf3b3-116">SSISDB データベースをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続されます。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-116">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="cf3b3-117">オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-117">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="cf3b3-118">**[SSISDB]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-118">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="cf3b3-119">プロパティを設定するプロジェクトが格納されているフォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-119">Expand the folder that contains the project that you want to set properties for.</span></span>  
  
5.  <span data-ttu-id="cf3b3-120">プロジェクトを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-120">Right-click the project, and then click **Properties**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="cf3b3-121">[全般] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="cf3b3-121">Set the options on the General page</span></span>  
 <span data-ttu-id="cf3b3-122">プロジェクトのプロパティを表示するには、[全般] ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-122">Use the General page to view project properties.</span></span>  
  
 <span data-ttu-id="cf3b3-123">**Name**</span><span class="sxs-lookup"><span data-stu-id="cf3b3-123">**Name**</span></span>  
 <span data-ttu-id="cf3b3-124">プロジェクト名を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-124">Lists the project name.</span></span>  
  
 <span data-ttu-id="cf3b3-125">**識別子**</span><span class="sxs-lookup"><span data-stu-id="cf3b3-125">**Identifier**</span></span>  
 <span data-ttu-id="cf3b3-126">プロジェクト ID を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-126">Lists the project ID.</span></span>  
  
 <span data-ttu-id="cf3b3-127">**説明**</span><span class="sxs-lookup"><span data-stu-id="cf3b3-127">**Description**</span></span>  
 <span data-ttu-id="cf3b3-128">プロジェクトの説明を表示します (省略可)。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-128">Displays the optional description of the project.</span></span>  
  
 <span data-ttu-id="cf3b3-129">**プロジェクトのバージョン**</span><span class="sxs-lookup"><span data-stu-id="cf3b3-129">**Project Version**</span></span>  
 <span data-ttu-id="cf3b3-130">プロジェクトのバージョンを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-130">Lists the project version.</span></span>  
  
 <span data-ttu-id="cf3b3-131">**配置日**</span><span class="sxs-lookup"><span data-stu-id="cf3b3-131">**Deployment Date**</span></span>  
 <span data-ttu-id="cf3b3-132">プロジェクトを配置または再配置した日付と時刻を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-132">Lists the date and time the project was deployed or redeployed.</span></span>  
  
##  <a name="set-the-options-on-the-permissions-page"></a><a name="permissions"></a> <span data-ttu-id="cf3b3-133">[権限] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="cf3b3-133">Set the options on the Permissions page</span></span>  
 <span data-ttu-id="cf3b3-134">プロジェクトの明示的な権限を表示および設定するには、 **[権限]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-134">Use the **Permissions** page to view and set explicit permissions for the project.</span></span>  
  
 <span data-ttu-id="cf3b3-135">参照</span><span class="sxs-lookup"><span data-stu-id="cf3b3-135">Browse</span></span>  
 <span data-ttu-id="cf3b3-136">**[参照]** をクリックすると、 **[すべてのプリンシパルを参照]** ダイアログ ボックスを使用して、権限を設定するユーザーおよびロールを選択できます。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-136">Click **Browse** to select users and roles that you want to set permissions for, by using the **Browse All Principals** dialog box.</span></span>  
  
 <span data-ttu-id="cf3b3-137">**Name**</span><span class="sxs-lookup"><span data-stu-id="cf3b3-137">**Name**</span></span>  
 <span data-ttu-id="cf3b3-138">ユーザーまたはロールの名前を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-138">Lists the name of the user or role.</span></span>  
  
 <span data-ttu-id="cf3b3-139">**Type**</span><span class="sxs-lookup"><span data-stu-id="cf3b3-139">**Type**</span></span>  
 <span data-ttu-id="cf3b3-140">ユーザーまたはロールの種類を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-140">Lists the type of user or role.</span></span>  
  
 <span data-ttu-id="cf3b3-141">**権限**</span><span class="sxs-lookup"><span data-stu-id="cf3b3-141">**Permission**</span></span>  
 <span data-ttu-id="cf3b3-142">権限を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-142">Lists the permissions.</span></span>  
  
 <span data-ttu-id="cf3b3-143">**Grantor**</span><span class="sxs-lookup"><span data-stu-id="cf3b3-143">**Grantor**</span></span>  
 <span data-ttu-id="cf3b3-144">権限を付与するユーザーまたはロールを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-144">Lists the user or role that grants the permission.</span></span>  
  
 <span data-ttu-id="cf3b3-145">**Grant**</span><span class="sxs-lookup"><span data-stu-id="cf3b3-145">**Grant**</span></span>  
 <span data-ttu-id="cf3b3-146">**[許可]** を選択すると、選択したユーザーまたはロールに対して権限が付与されます。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-146">When **Grant** is selected, the permission is granted for the selected user or role.</span></span>  
  
 <span data-ttu-id="cf3b3-147">**Deny**</span><span class="sxs-lookup"><span data-stu-id="cf3b3-147">**Deny**</span></span>  
 <span data-ttu-id="cf3b3-148">**[拒否]** を選択すると、選択したユーザーまたはロールに対する権限が拒否されます。</span><span class="sxs-lookup"><span data-stu-id="cf3b3-148">When **Deny** is selected, the permission is denied for the selected user or role.</span></span>  
  
  
