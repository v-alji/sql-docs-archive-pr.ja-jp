---
title: '[構成] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.SSIS.SSMS.ISPROJECTPROP.PARAMETERS.F1
- SQL12.SSIS.SSMS.ISPROJECTPROP.REFERENCES.F1
- sql12.dts.designer.configure.f1
ms.assetid: 10183c8d-b1be-420f-972a-96ea97d4f4d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 857baf3421f2744144e10b0df0b770538f533192
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642252"
---
# <a name="configure-dialog-box"></a><span data-ttu-id="9a7f0-102">[構成] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="9a7f0-102">Configure Dialog Box</span></span>
  <span data-ttu-id="9a7f0-103">パッケージとプロジェクトのパラメーター、接続マネージャー、および環境への参照を構成するには、 **[構成]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-103">Use the **Configure** dialog box to configure parameters, connection managers, and references to environments, for packages and projects.</span></span>  
  
 <span data-ttu-id="9a7f0-104">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="9a7f0-104">**What do you want to do?**</span></span>  
  
-   <span data-ttu-id="9a7f0-105">[[構成] ダイアログ ボックスを開く](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="9a7f0-105">[Open the Configure Dialog Box](#open_dialog)</span></span>  
  
-   <span data-ttu-id="9a7f0-106">[[パラメーター] ページのオプションの設定](#parameter)</span><span class="sxs-lookup"><span data-stu-id="9a7f0-106">[Set the options on the Parameters page](#parameter)</span></span>  
  
-   <span data-ttu-id="9a7f0-107">[[参照] ページのオプションの設定](#references)</span><span class="sxs-lookup"><span data-stu-id="9a7f0-107">[Set the options on the References page](#references)</span></span>  
  
##  <a name="open-the-configure-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="9a7f0-108">[構成] ダイアログ ボックスを開く</span><span class="sxs-lookup"><span data-stu-id="9a7f0-108">Open the Configure Dialog Box</span></span>  
  
1.  <span data-ttu-id="9a7f0-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="9a7f0-110">SSISDB データベースをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続されます。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-110">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="9a7f0-111">オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="9a7f0-112">**[SSISDB]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-112">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="9a7f0-113">構成するパッケージまたはプロジェクトが格納されているフォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-113">Expand the folder that contains the package or project that you want to configure.</span></span>  
  
5.  <span data-ttu-id="9a7f0-114">パッケージまたはプロジェクトを右クリックし、 **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-114">Right-click the package or project, and then click **Configure**.</span></span>  
  
##  <a name="set-the-options-on-the-parameters-page"></a><a name="parameter"></a> <span data-ttu-id="9a7f0-115">[パラメーター] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="9a7f0-115">Set the options on the Parameters page</span></span>  
 <span data-ttu-id="9a7f0-116">パラメーターの名前と値を表示したり、値を変更するには、 **[パラメーター]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-116">Use the **Parameters** page to view parameter names and values, and to modify the values.</span></span>  
  
 <span data-ttu-id="9a7f0-117">**[スコープ]** ボックスの一覧から、 **[パラメーター]** タブと **[接続マネージャー]** タブに表示されるパラメーターのスコープを選択します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-117">Select the scope of the parameters displayed in the **Parameters** and **Connection Managers** tabs, in the **Scope** drop-down list.</span></span>  
  
 <span data-ttu-id="9a7f0-118">**[パラメーター]** タブのオプションの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-118">The following is a list of the options in the **Parameters** tab.</span></span>  
  
 <span data-ttu-id="9a7f0-119">**コンテナー**</span><span class="sxs-lookup"><span data-stu-id="9a7f0-119">**Container**</span></span>  
 <span data-ttu-id="9a7f0-120">パラメーターを含むオブジェクトを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-120">Lists the object that contains the parameter.</span></span>  
  
 <span data-ttu-id="9a7f0-121">**名前**</span><span class="sxs-lookup"><span data-stu-id="9a7f0-121">**Name**</span></span>  
 <span data-ttu-id="9a7f0-122">パラメーター名を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-122">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="9a7f0-123">**Value**</span><span class="sxs-lookup"><span data-stu-id="9a7f0-123">**Value**</span></span>  
 <span data-ttu-id="9a7f0-124">パラメーター値を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-124">Lists the parameter value.</span></span> <span data-ttu-id="9a7f0-125">**[パラメーター値の設定]** ダイアログ ボックスの値を変更するには、参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-125">Click the ellipsis button to change the value in the **Set Parameter Value** dialog box.</span></span>  
  
 <span data-ttu-id="9a7f0-126">**[接続マネージャー]** タブのオプションの一覧を次に示します。このタブは、接続マネージャーのプロパティの値を変更するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-126">The following is a list of the options in the **Connection Managers** tab. You use this tab to change values for connection manager properties.</span></span> <span data-ttu-id="9a7f0-127">パラメーターは、SSIS サーバー上でプロパティ用に自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-127">Parameters are automatically generated on the SSIS server for the properties.</span></span>  
  
 <span data-ttu-id="9a7f0-128">**コンテナー**</span><span class="sxs-lookup"><span data-stu-id="9a7f0-128">**Container**</span></span>  
 <span data-ttu-id="9a7f0-129">接続マネージャーを含むオブジェクトを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-129">Lists the object that contains the connection manager.</span></span>  
  
 <span data-ttu-id="9a7f0-130">**名前**</span><span class="sxs-lookup"><span data-stu-id="9a7f0-130">**Name**</span></span>  
 <span data-ttu-id="9a7f0-131">接続マネージャーの名前を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-131">Lists the connection manager name.</span></span>  
  
 <span data-ttu-id="9a7f0-132">**プロパティ名**</span><span class="sxs-lookup"><span data-stu-id="9a7f0-132">**Property name**</span></span>  
 <span data-ttu-id="9a7f0-133">接続マネージャーのプロパティの名前を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-133">Lists the name of the connection manager property.</span></span>  
  
 <span data-ttu-id="9a7f0-134">**Value**</span><span class="sxs-lookup"><span data-stu-id="9a7f0-134">**Value**</span></span>  
 <span data-ttu-id="9a7f0-135">接続マネージャーのプロパティに割り当てられた値を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-135">Lists the value assigned to the connection manager property.</span></span> <span data-ttu-id="9a7f0-136">**[パラメーター値の設定]** ダイアログ ボックスの値を変更するには、参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-136">Click the ellipsis button to change the value in the **Set Parameter Value** dialog box.</span></span> <span data-ttu-id="9a7f0-137">リテラル値を入力するか、使用する値を含んでいる環境変数をマップするか、パッケージの既定値を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-137">You can enter a literal value, map an environment variable that contains the value you want to use, or use the default value from the package.</span></span>  
  
##  <a name="set-the-options-on-the-references-page"></a><a name="references"></a> <span data-ttu-id="9a7f0-138">[参照] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="9a7f0-138">Set the options on the References page</span></span>  
 <span data-ttu-id="9a7f0-139">環境への参照を追加および削除したり、環境プロパティにアクセスするには、 **[参照]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-139">Use the **References** page to add and remove references to environments, and to access environment properties.</span></span>  
  
 <span data-ttu-id="9a7f0-140">環境は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置したプロジェクトに含まれるパッケージのランタイム値を示します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-140">An environment specifies runtime values for packages contained in the projects you've deployed to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="9a7f0-141">**Environment**</span><span class="sxs-lookup"><span data-stu-id="9a7f0-141">**Environment**</span></span>  
 <span data-ttu-id="9a7f0-142">環境を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-142">Lists the environment.</span></span>  
  
 <span data-ttu-id="9a7f0-143">**環境フォルダー**</span><span class="sxs-lookup"><span data-stu-id="9a7f0-143">**Environment Folder**</span></span>  
 <span data-ttu-id="9a7f0-144">環境を含むフォルダーを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-144">Lists the folder that contains the environment.</span></span>  
  
 <span data-ttu-id="9a7f0-145">**[ファイル]**</span><span class="sxs-lookup"><span data-stu-id="9a7f0-145">**Open**</span></span>  
 <span data-ttu-id="9a7f0-146">**[環境のプロパティ]** ダイアログ ボックスを開く場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-146">Click to open the **Environment Properties** dialog box.</span></span>  
  
 <span data-ttu-id="9a7f0-147">**追加**</span><span class="sxs-lookup"><span data-stu-id="9a7f0-147">**Add**</span></span>  
 <span data-ttu-id="9a7f0-148">環境への参照を追加する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-148">Click to add a reference to an environment.</span></span> <span data-ttu-id="9a7f0-149">**[環境の参照]** ダイアログ ボックスで、環境をクリックして **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-149">In the **Browse Environments** dialog box click an environment and then click **OK**.</span></span>  
  
 <span data-ttu-id="9a7f0-150">**SSISDB** ノードの下の任意のプロジェクト フォルダーに含まれている環境を選択できます。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-150">You can select an environment contained in any project folder under the **SSISDB** node.</span></span>  
  
 <span data-ttu-id="9a7f0-151">**Remove**</span><span class="sxs-lookup"><span data-stu-id="9a7f0-151">**Remove**</span></span>  
 <span data-ttu-id="9a7f0-152">**[参照]** 領域に表示されている環境を選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a7f0-152">Click an environment listed in the **References** area, and then click **Remove**.</span></span>  
  
  
