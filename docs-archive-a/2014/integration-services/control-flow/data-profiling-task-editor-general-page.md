---
title: '[データ プロファイル タスク エディター] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataprofilingtask.general.f1
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: eec15906-d757-4079-b2f6-aca4e52b3b4c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4cfcdf472f817d3dd688a5f867ac74d46835ab91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642227"
---
# <a name="data-profiling-task-editor-general-page"></a><span data-ttu-id="5986e-102">[データ プロファイル タスク エディター] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="5986e-102">Data Profiling Task Editor (General Page)</span></span>
  <span data-ttu-id="5986e-103">**[データ プロファイル タスク エディター]** の **[全般]** ページを使用すると、次のオプションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="5986e-103">Use the **General** page of the **Data Profiling Task Editor** to configure the following options:</span></span>  
  
-   <span data-ttu-id="5986e-104">プロファイル出力の保存先を指定する。</span><span class="sxs-lookup"><span data-stu-id="5986e-104">Specify the destination for the profile output.</span></span>  
  
-   <span data-ttu-id="5986e-105">既定の設定を使用して、単一のテーブルまたはビューをプロファイルするタスクを簡素化する。</span><span class="sxs-lookup"><span data-stu-id="5986e-105">Use the default settings to simplify the task of profiling a single table or view.</span></span>  
  
 <span data-ttu-id="5986e-106">データ プロファイル タスクの使用方法の詳細については、「 [データ プロファイル タスクのセットアップ](data-profiling-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5986e-106">For more information about how to use the Data Profiling task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="5986e-107">Data Profile Viewer を使用してデータ プロファイル タスクの出力を分析する方法の詳細については、「 [Data Profile Viewer](data-profile-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5986e-107">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
 <span data-ttu-id="5986e-108">**[データ プロファイル タスク エディター] の [全般] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="5986e-108">**To open the General page of the Data Profiling Task Editor**</span></span>  
  
1.  <span data-ttu-id="5986e-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、データ プロファイル タスクを含む [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="5986e-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that has the Data Profiling task.</span></span>  
  
2.  <span data-ttu-id="5986e-110">**[制御フロー]** タブで、データ プロファイル タスクをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="5986e-110">On the **Control Flow** tab, double-click the Data Profiling task.</span></span>  
  
3.  <span data-ttu-id="5986e-111">**[データ プロファイル タスク エディター]** で、 **[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5986e-111">In the **Data Profiling Task Editor**, click **General**.</span></span>  
  
## <a name="data-profiling-options"></a><span data-ttu-id="5986e-112">データ プロファイルに関するオプション</span><span class="sxs-lookup"><span data-stu-id="5986e-112">Data Profiling Options</span></span>  
 <span data-ttu-id="5986e-113">**タイムアウト**</span><span class="sxs-lookup"><span data-stu-id="5986e-113">**Timeout**</span></span>  
 <span data-ttu-id="5986e-114">データ プロファイル タスクがタイムアウトして実行を停止するまでの秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5986e-114">Specify the number of seconds after which the Data Profiling task should timeout and stop running.</span></span> <span data-ttu-id="5986e-115">既定値は 0 であり、タイムアウトしないことを示します。</span><span class="sxs-lookup"><span data-stu-id="5986e-115">The default value is 0, which indicates no timeout.</span></span>  
  
## <a name="destination-options"></a><span data-ttu-id="5986e-116">転送先に関するオプション</span><span class="sxs-lookup"><span data-stu-id="5986e-116">Destination Options</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5986e-117">出力ファイルには、データベースに関する機密データやデータベースに格納されているデータが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5986e-117">The output file might contain sensitive data about your database and the data that database contains.</span></span> <span data-ttu-id="5986e-118">このファイルの安全性を高める方法の推奨事項については、「 [パッケージで使用されるファイルへのアクセス](../access-to-files-used-by-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5986e-118">For suggestions about how to make this file more secure, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
 <span data-ttu-id="5986e-119">**[DestinationType]**</span><span class="sxs-lookup"><span data-stu-id="5986e-119">**DestinationType**</span></span>  
 <span data-ttu-id="5986e-120">データ プロファイル出力をファイルに保存するか変数に保存するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5986e-120">Specify whether to save the data profile output to a file or a variable:</span></span>  
  
|<span data-ttu-id="5986e-121">値</span><span class="sxs-lookup"><span data-stu-id="5986e-121">Value</span></span>|<span data-ttu-id="5986e-122">説明</span><span class="sxs-lookup"><span data-stu-id="5986e-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5986e-123">**[FileConnection]**</span><span class="sxs-lookup"><span data-stu-id="5986e-123">**FileConnection**</span></span>|<span data-ttu-id="5986e-124">ファイル接続マネージャーで指定された場所にあるファイルにプロファイル出力を保存します。</span><span class="sxs-lookup"><span data-stu-id="5986e-124">Save the profile output to a file in the location that is specified in a File connection manager.</span></span><br /><br /> <span data-ttu-id="5986e-125">注: 使用するファイル接続マネージャーは **[Destination]** オプションで指定します。</span><span class="sxs-lookup"><span data-stu-id="5986e-125">Note: You specify which File connection manager to use in the **Destination** option.</span></span>|  
|<span data-ttu-id="5986e-126">**変数**</span><span class="sxs-lookup"><span data-stu-id="5986e-126">**Variable**</span></span>|<span data-ttu-id="5986e-127">プロファイル出力をパッケージ変数に保存します。</span><span class="sxs-lookup"><span data-stu-id="5986e-127">Save the profile output to a package variable.</span></span><br /><br /> <span data-ttu-id="5986e-128">注: 使用するパッケージ変数は **[Destination]** オプションで指定します。</span><span class="sxs-lookup"><span data-stu-id="5986e-128">Note: You specify which package variable to use in the **Destination** option.</span></span>|  
  
 <span data-ttu-id="5986e-129">**宛先**</span><span class="sxs-lookup"><span data-stu-id="5986e-129">**Destination**</span></span>  
 <span data-ttu-id="5986e-130">データ プロファイル出力を含むファイル接続マネージャーまたはパッケージ変数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5986e-130">Specify which File connection manager or package variable contains the data profile output:</span></span>  
  
-   <span data-ttu-id="5986e-131">**[DestinationType]** オプションが **[FileConnection]** に設定されている場合、 **[Destination]** オプションには使用可能なファイル接続マネージャーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5986e-131">If the **DestinationType** option is set to **FileConnection**, the **Destination** option displays the available File connection managers.</span></span> <span data-ttu-id="5986e-132">これらの接続マネージャーのいずれかを選択するか、[\<New File connection>] を選択して新しいファイル接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="5986e-132">Select one of these connection managers, or select \<New File connection> to create a new File connection manager.</span></span>  
  
-   <span data-ttu-id="5986e-133">**[DestinationType]** オプションが **[Variable]** に設定されている場合、 **[Destination]** オプションでは使用可能なパッケージ変数が **[Destination]** の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5986e-133">If the **DestinationType** option is set to **Variable**, the **Destination** option displays the available package variables in the **Destination** list.</span></span> <span data-ttu-id="5986e-134">これらの変数のいずれかを選択するか、[\<New Variable>] を選択して新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="5986e-134">Select one of these variables, or select \<New Variable> to create a new variable.</span></span>  
  
 <span data-ttu-id="5986e-135">**[OverwriteDestination]**</span><span class="sxs-lookup"><span data-stu-id="5986e-135">**OverwriteDestination**</span></span>  
 <span data-ttu-id="5986e-136">出力ファイルが既に存在する場合に、その出力ファイルを上書きするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5986e-136">Specify whether to overwrite the output file if it already exists.</span></span> <span data-ttu-id="5986e-137">既定値は **False**です。</span><span class="sxs-lookup"><span data-stu-id="5986e-137">The default value is **False**.</span></span> <span data-ttu-id="5986e-138">このプロパティの値は、[DestinationType] オプションが [FileConnection] に設定されている場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="5986e-138">The value of this property is used only when the DestinationType option is set to FileConnection.</span></span> <span data-ttu-id="5986e-139">[DestinationType] オプションが [Variable] に設定されている場合は、変数の以前の値が常に上書きされます。</span><span class="sxs-lookup"><span data-stu-id="5986e-139">When the DestinationType option is set to Variable, the task always overwrites the previous value of the variable.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5986e-140">出力ファイル名を変更せずに、または **OverwriteDestination** プロパティの値を **True**に変更せずに、データ プロファイル タスクを 2 回以上実行すると、出力ファイルが既に存在するというメッセージが表示され、タスクは失敗します。</span><span class="sxs-lookup"><span data-stu-id="5986e-140">If you try to run the Data Profiling task more than once without changing the output file name or changing the value of the **OverwriteDestination** property to **True**, the task fails with the message that the output file already exists.</span></span>  
  
## <a name="other-options"></a><span data-ttu-id="5986e-141">その他のオプション</span><span class="sxs-lookup"><span data-stu-id="5986e-141">Other Options</span></span>  
 <span data-ttu-id="5986e-142">**[クイック プロファイル]**</span><span class="sxs-lookup"><span data-stu-id="5986e-142">**Quick Profile**</span></span>  
 <span data-ttu-id="5986e-143">**[単一テーブル クイック プロファイル フォーム]** を表示します。</span><span class="sxs-lookup"><span data-stu-id="5986e-143">Display the **Single Table Quick Profile Form**.</span></span> <span data-ttu-id="5986e-144">このフォームでは、既定の設定を使用することで、単一のテーブルまたはビューをプロファイルするタスクを簡素化します。</span><span class="sxs-lookup"><span data-stu-id="5986e-144">This form simplifies the task of profiling a single table or view by using default settings.</span></span> <span data-ttu-id="5986e-145">詳細については、「 [単一テーブル クイック プロファイル フォーム &#40;データ プロファイル タスク&#41;](single-table-quick-profile-form-data-profiling-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5986e-145">For more information, see [Single Table Quick Profile Form &#40;Data Profiling Task&#41;](single-table-quick-profile-form-data-profiling-task.md).</span></span>  
  
 <span data-ttu-id="5986e-146">**[プロファイル ビューアーを開く]**</span><span class="sxs-lookup"><span data-stu-id="5986e-146">**Open Profile Viewer**</span></span>  
 <span data-ttu-id="5986e-147">Data Profile Viewer を開きます。</span><span class="sxs-lookup"><span data-stu-id="5986e-147">Opens the Data Profile Viewer.</span></span> <span data-ttu-id="5986e-148">スタンドアロンの Data Profile Viewer は、データ プロファイル タスクのデータ プロファイル出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="5986e-148">The stand-alone Data Profile Viewer displays data profile output from the Data Profiling task.</span></span> <span data-ttu-id="5986e-149">データ プロファイル出力は、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ内でデータ プロファイル タスクを実行してデータ プロファイルを計算した後に表示できます。</span><span class="sxs-lookup"><span data-stu-id="5986e-149">You can view the data profile output after you have run the Data Profiling task inside the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package and computed the data profiles.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5986e-150">Data Profile Viewer を開くには、 *\<drive>* :\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn フォルダーの DataProfileViewer.exe を実行する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="5986e-150">You can also open the Data Profile Viewer by running the DataProfileViewer.exe in the folder, *\<drive>*:\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5986e-151">参照</span><span class="sxs-lookup"><span data-stu-id="5986e-151">See Also</span></span>  
 <span data-ttu-id="5986e-152">[単一テーブル クイック プロファイル フォーム &#40;データ プロファイル タスク&#41;](single-table-quick-profile-form-data-profiling-task.md) </span><span class="sxs-lookup"><span data-stu-id="5986e-152">[Single Table Quick Profile Form &#40;Data Profiling Task&#41;](single-table-quick-profile-form-data-profiling-task.md) </span></span>  
 <span data-ttu-id="5986e-153">[データ プロファイル タスク エディター &#40;[プロファイル要求] ページ&#41;](data-profiling-task-editor-profile-requests-page.md)</span><span class="sxs-lookup"><span data-stu-id="5986e-153">[Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md)</span></span>  
  
  
