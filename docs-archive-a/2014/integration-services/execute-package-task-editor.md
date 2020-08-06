---
title: パッケージ実行タスクエディター |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executepackagetask.parameter.F1
- sql12.dts.designer.executepackagetask.package.f1
- sql12.dts.designer.executepackagetask.general.f1
ms.assetid: c2c96b4f-eb10-4d8b-be34-88edfd0785fb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9b2e18516e1f5c1b7af56bd1e84ef875557fd49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641756"
---
# <a name="execute-package-task-editor"></a><span data-ttu-id="ebd0f-102">パッケージ実行タスク エディター</span><span class="sxs-lookup"><span data-stu-id="ebd0f-102">Execute Package Task Editor</span></span>
  <span data-ttu-id="ebd0f-103">パッケージ実行タスクを構成するには、パッケージ実行タスク エディターを使用します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-103">Use the Execute Package Task Editor to configure the Execute Package Task.</span></span> <span data-ttu-id="ebd0f-104">パッケージ実行タスクは、パッケージのワークフローの一部として他のパッケージを実行できるようにすることで、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のエンタープライズ用機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-104">The Execute Package task extends the enterprise capabilities of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] by letting packages run other packages as part of a workflow.</span></span>  
  
 <span data-ttu-id="ebd0f-105">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-105">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="ebd0f-106">パッケージ実行タスク エディターを開く</span><span class="sxs-lookup"><span data-stu-id="ebd0f-106">Open the Execute Package Task Editor</span></span>](#open)  
  
-   <span data-ttu-id="ebd0f-107">[[全般] ページのオプションを設定する](#general)</span><span class="sxs-lookup"><span data-stu-id="ebd0f-107">[Set the Options on the General Page](#general)</span></span>  
  
-   <span data-ttu-id="ebd0f-108">[[パッケージ] ページのオプションを設定する](#package)</span><span class="sxs-lookup"><span data-stu-id="ebd0f-108">[Set the Options on the Package Page](#package)</span></span>  
  
-   <span data-ttu-id="ebd0f-109">[[パラメーター バインド] ページのオプションを設定する](#parameter)</span><span class="sxs-lookup"><span data-stu-id="ebd0f-109">[Set the Options on the Parameter Bindings Page](#parameter)</span></span>  
  
##  <a name="open-the-execute-package-task-editor"></a><a name="open"></a> <span data-ttu-id="ebd0f-110">パッケージ実行タスク エディターを開く</span><span class="sxs-lookup"><span data-stu-id="ebd0f-110">Open the Execute Package Task Editor</span></span>  
  
1.  <span data-ttu-id="ebd0f-111">パッケージ実行タスクが含まれる [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] で開きます。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-111">Open an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] that contains an Execute Package task.</span></span>  
  
2.  <span data-ttu-id="ebd0f-112">SSIS デザイナーでタスクを右クリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-112">Right-click the task in the SSIS Designer, and then click **Edit**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="ebd0f-113">[全般] ページのオプションを設定する</span><span class="sxs-lookup"><span data-stu-id="ebd0f-113">Set the Options on the General Page</span></span>  
 <span data-ttu-id="ebd0f-114">**名前**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-114">**Name**</span></span>  
 <span data-ttu-id="ebd0f-115">パッケージ実行タスクの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-115">Provide a unique name for the Execute Package task.</span></span> <span data-ttu-id="ebd0f-116">この名前は、タスク アイコンのラベルとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-116">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebd0f-117">タスク名はパッケージ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-117">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="ebd0f-118">**説明**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-118">**Description**</span></span>  
 <span data-ttu-id="ebd0f-119">パッケージ実行タスクの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-119">Type a description of the Execute Package task.</span></span>  
  
##  <a name="set-the-options-on-the-package-page"></a><a name="package"></a> <span data-ttu-id="ebd0f-120">[パッケージ] ページのオプションを設定する</span><span class="sxs-lookup"><span data-stu-id="ebd0f-120">Set the Options on the Package Page</span></span>  
 <span data-ttu-id="ebd0f-121">**ReferenceType**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-121">**ReferenceType**</span></span>  
 <span data-ttu-id="ebd0f-122">プロジェクト内の子パッケージの場合は **[プロジェクト参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-122">Select **Project Reference** for child packages that are in the project.</span></span> <span data-ttu-id="ebd0f-123">パッケージの外部にある子パッケージの場合は **[外部参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-123">Select **External Reference** for child packages that are located outside the package</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebd0f-124">**[ReferenceType]** オプションは読み取り専用であり、対象パッケージを含むプロジェクトがプロジェクト配置モデルに変換されていない場合は **[外部参照]** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-124">The **ReferenceType** option is ready-only and set to **External Reference** if the project that contains the package has not been converted to the project deployment model.</span></span> <span data-ttu-id="ebd0f-125">変換の詳細については、「 [Integration Services サーバーへのプロジェクトの配置](../../2014/integration-services/deploy-projects-to-integration-services-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-125">For more information about conversion, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="ebd0f-126">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-126">**Password**</span></span>  
 <span data-ttu-id="ebd0f-127">子パッケージがパスワードで保護されている場合は、子パッケージのパスワードを入力するか、参照ボタン [...] をクリックして子パッケージの新しいパスワードを作成します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-127">If the child package is password protected, provide the password for the child package, or click the ellipsis button (...) and create a new password for the child package.</span></span>  
  
 `ExecuteOutOfProcess`  
 <span data-ttu-id="ebd0f-128">子パッケージが親パッケージのプロセス内で実行するか、または別のプロセスで実行するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-128">Specify whether the child package runs in the process of the parent package or in a separate process.</span></span> <span data-ttu-id="ebd0f-129">既定では、パッケージ実行タスクの ExecuteOutOfProcess プロパティはに設定され、 `False` 子パッケージは親パッケージと同じプロセスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-129">By default, the ExecuteOutOfProcess property of the Execute Package task is set to `False`, and the child package runs in the same process as the parent package.</span></span> <span data-ttu-id="ebd0f-130">このプロパティを `true` に設定すると、子パッケージは別のプロセスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-130">If you set this property to `true`, the child package runs in a separate process.</span></span> <span data-ttu-id="ebd0f-131">これにより、子パッケージの起動が遅くなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-131">This may slow down the launching of the child package.</span></span> <span data-ttu-id="ebd0f-132">また、プロパティを `true` に設定した場合、ツールのみのインストールではパッケージをデバッグできません。[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 製品をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-132">In addition, if set the property to `true`, you cannot debug the package in a tools-only install; you must install the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] product.</span></span> <span data-ttu-id="ebd0f-133">詳細については、「 [Integration Services のインストール](install-windows/install-integration-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-133">For more information, see [Install Integration Services](install-windows/install-integration-services.md).</span></span>  
  
### <a name="referencetype-dynamic-options"></a><span data-ttu-id="ebd0f-134">[ReferenceType] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="ebd0f-134">ReferenceType Dynamic Options</span></span>  
  
#### <a name="referencetype--external-reference"></a><span data-ttu-id="ebd0f-135">ReferenceType = 外部参照</span><span class="sxs-lookup"><span data-stu-id="ebd0f-135">ReferenceType = External Reference</span></span>  
 <span data-ttu-id="ebd0f-136">**場所**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-136">**Location**</span></span>  
 <span data-ttu-id="ebd0f-137">子パッケージの場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-137">Select the location of the child package.</span></span> <span data-ttu-id="ebd0f-138">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-138">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="ebd0f-139">値</span><span class="sxs-lookup"><span data-stu-id="ebd0f-139">Value</span></span>|<span data-ttu-id="ebd0f-140">説明</span><span class="sxs-lookup"><span data-stu-id="ebd0f-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ebd0f-141">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-141">**SQL Server**</span></span>|<span data-ttu-id="ebd0f-142">場所を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-142">Set the location to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>|  
|<span data-ttu-id="ebd0f-143">**ファイル システム**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-143">**File system**</span></span>|<span data-ttu-id="ebd0f-144">場所をファイル システムに設定します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-144">Set the location to the file system.</span></span>|  
  
 <span data-ttu-id="ebd0f-145">**接続**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-145">**Connection**</span></span>  
 <span data-ttu-id="ebd0f-146">子パッケージの格納場所の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-146">Select the type of storage location for the child package.</span></span>  
  
 <span data-ttu-id="ebd0f-147">**PackageNameReadOnly**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-147">**PackageNameReadOnly**</span></span>  
 <span data-ttu-id="ebd0f-148">パッケージ名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-148">Displays the package name.</span></span>  
  
#### <a name="referencetype--project-reference"></a><span data-ttu-id="ebd0f-149">ReferenceType = プロジェクト参照</span><span class="sxs-lookup"><span data-stu-id="ebd0f-149">ReferenceType = Project Reference</span></span>  
 <span data-ttu-id="ebd0f-150">**PackageNameFromProjectReference**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-150">**PackageNameFromProjectReference**</span></span>  
 <span data-ttu-id="ebd0f-151">プロジェクトに含まれるパッケージで子パッケージにするものを選択します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-151">Select a package contained in the project, to be the child package.</span></span>  
  
### <a name="location-dynamic-options"></a><span data-ttu-id="ebd0f-152">[Location] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="ebd0f-152">Location Dynamic Options</span></span>  
  
#### <a name="location--sql-server"></a><span data-ttu-id="ebd0f-153">Location = SQL Server</span><span class="sxs-lookup"><span data-stu-id="ebd0f-153">Location = SQL Server</span></span>  
 <span data-ttu-id="ebd0f-154">**接続**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-154">**Connection**</span></span>  
 <span data-ttu-id="ebd0f-155">OLE DB 接続マネージャーを一覧から選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-155">Select an OLE DB connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="ebd0f-156">**関連トピック:** [OLE DB 接続マネージャー](connection-manager/ole-db-connection-manager.md)、 [OLE DB 接続マネージャーの構成](../../2014/integration-services/configure-ole-db-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="ebd0f-156">**Related Topics:** [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md), [Configure OLE DB Connection Manager](../../2014/integration-services/configure-ole-db-connection-manager.md)</span></span>  
  
 <span data-ttu-id="ebd0f-157">**PackageName**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-157">**PackageName**</span></span>  
 <span data-ttu-id="ebd0f-158">子パッケージの名前を入力するか、[...] をクリックし、パッケージを指定します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-158">Type the name of the child package, or click the ellipsis (...) and then locate the package.</span></span>  
  
#### <a name="location--file-system"></a><span data-ttu-id="ebd0f-159">Location = ファイル システム</span><span class="sxs-lookup"><span data-stu-id="ebd0f-159">Location = File system</span></span>  
 <span data-ttu-id="ebd0f-160">**接続**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-160">**Connection**</span></span>  
 <span data-ttu-id="ebd0f-161">一覧でファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-161">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="ebd0f-162">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="ebd0f-162">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="ebd0f-163">**PackageNameReadOnly**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-163">**PackageNameReadOnly**</span></span>  
 <span data-ttu-id="ebd0f-164">パッケージ名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-164">Displays the package name.</span></span>  
  
##  <a name="set-the-options-on-the-parameter-bindings-page"></a><a name="parameter"></a> <span data-ttu-id="ebd0f-165">[パラメーター バインド] ページのオプションを設定する</span><span class="sxs-lookup"><span data-stu-id="ebd0f-165">Set the Options on the Parameter Bindings Page</span></span>  
 <span data-ttu-id="ebd0f-166">親パッケージまたはプロジェクトから子パッケージに値を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-166">You can pass values from the parent package or the project, to the child package.</span></span> <span data-ttu-id="ebd0f-167">プロジェクトはプロジェクト配置モデルを使用し、子パッケージが親パッケージと同じプロジェクトに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-167">The project must use the project deployment model and the child package must be contained in the same project that contains the parent package.</span></span>  
  
 <span data-ttu-id="ebd0f-168">プロジェクト配置モデルへのプロジェクトの変換に関する詳細については、「 [Integration Services サーバーへのプロジェクトの配置](../../2014/integration-services/deploy-projects-to-integration-services-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-168">For information about converting projects to the project deployment model, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="ebd0f-169">**子パッケージのパラメーター**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-169">**Child package parameter**</span></span>  
 <span data-ttu-id="ebd0f-170">子パッケージのパラメーターの名前を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-170">Enter or select a name for the child package parameter.</span></span>  
  
 <span data-ttu-id="ebd0f-171">**バインドするパラメーターまたは変数**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-171">**Binding parameter or variable**</span></span>  
 <span data-ttu-id="ebd0f-172">子パッケージに渡す値を含むパラメーターまたは変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-172">Select the parameter or variable that contains the value that you want to pass to the child package.</span></span>  
  
 <span data-ttu-id="ebd0f-173">**追加**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-173">**Add**</span></span>  
 <span data-ttu-id="ebd0f-174">パラメーターまたは変数を子パッケージのパラメーターにマップする場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-174">Click to map a parameter or variable to a child package parameter.</span></span>  
  
 <span data-ttu-id="ebd0f-175">**Remove**</span><span class="sxs-lookup"><span data-stu-id="ebd0f-175">**Remove**</span></span>  
 <span data-ttu-id="ebd0f-176">パラメーターまたは変数と子パッケージのパラメーターの間のマッピングを削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebd0f-176">Click to remove a mapping between a parameter or variable and a child package parameter.</span></span>  
  
  
