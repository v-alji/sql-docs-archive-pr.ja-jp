---
title: '[Raw ファイル変換先エディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledestinationconnectionmanager.f1
ms.assetid: a0ec9643-3b44-4467-b855-f45ae4794f7f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a693591921a5669eb9bc8160f0be076ab4d6869b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713273"
---
# <a name="raw-file-destination-editor-connection-manager-page"></a><span data-ttu-id="0d50e-102">[RAW ファイル変換先エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="0d50e-102">Raw File Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="0d50e-103">ファイルに RAW データを書き込むための RAW ファイル変換先を構成するには、RAW ファイル変換先エディターを使用します。</span><span class="sxs-lookup"><span data-stu-id="0d50e-103">Use the Raw File Destination Editor to configure the Raw File destination to write raw data to a file.</span></span>  
  
 <span data-ttu-id="0d50e-104">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="0d50e-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="0d50e-105">Raw ファイル変換先エディターを開く</span><span class="sxs-lookup"><span data-stu-id="0d50e-105">Open the Raw File Destination Editor</span></span>](#open)  
  
-   <span data-ttu-id="0d50e-106">[[接続マネージャー] タブのオプションの設定](#connection)</span><span class="sxs-lookup"><span data-stu-id="0d50e-106">[Set options on the Connection Manager tab](#connection)</span></span>  
  
-   <span data-ttu-id="0d50e-107">[[列] タブのオプションの設定](#mapping)</span><span class="sxs-lookup"><span data-stu-id="0d50e-107">[Set options on the Columns tab](#mapping)</span></span>  
  
##  <a name="open-the-raw-file-destination-editor"></a><a name="open"></a> <span data-ttu-id="0d50e-108">RAW ファイル変換先エディターを開く</span><span class="sxs-lookup"><span data-stu-id="0d50e-108">Open the Raw File Destination Editor</span></span>  
  
1.  <span data-ttu-id="0d50e-109">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]パッケージに RAW ファイル変換先を追加します。</span><span class="sxs-lookup"><span data-stu-id="0d50e-109">Add the Raw File destination to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="0d50e-110">コンポーネントを右クリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d50e-110">Right-click the component and then click **Edit**.</span></span>  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> <span data-ttu-id="0d50e-111">[接続マネージャー] タブのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="0d50e-111">Set options on the Connection Manager tab</span></span>  
 <span data-ttu-id="0d50e-112">**アクセス モード**</span><span class="sxs-lookup"><span data-stu-id="0d50e-112">**Access mode**</span></span>  
 <span data-ttu-id="0d50e-113">ファイル名の指定方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="0d50e-113">Select how the file name is specified.</span></span> <span data-ttu-id="0d50e-114">ファイル名とパスを直接入力するには **[ファイル名]** を選択します。ファイル名を含んでいる変数を指定するには、 **[変数からのファイル名]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0d50e-114">Select **File name** to enter the file name and path directly, of **File name from variable** to specify a variable that contains the file name.</span></span>  
  
 <span data-ttu-id="0d50e-115">**[ファイル名]** または **[変数名]**</span><span class="sxs-lookup"><span data-stu-id="0d50e-115">**File name** or **Variable name**</span></span>  
 <span data-ttu-id="0d50e-116">RAW ファイルの名前とパスを入力するか、またはファイル名を含んでいる変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="0d50e-116">Enter the name and path of the raw file, or select the variable that contains the file name.</span></span>  
  
 <span data-ttu-id="0d50e-117">**[書き込みオプション]**</span><span class="sxs-lookup"><span data-stu-id="0d50e-117">**Write option**</span></span>  
 <span data-ttu-id="0d50e-118">ファイルの作成およびファイルへの書き込みに使用するメソッドを選択します。</span><span class="sxs-lookup"><span data-stu-id="0d50e-118">Select the method used to create and write to the file.</span></span>  
  
 <span data-ttu-id="0d50e-119">**[初期 RAW ファイルの生成]**</span><span class="sxs-lookup"><span data-stu-id="0d50e-119">**Generate initial raw file**</span></span>  
 <span data-ttu-id="0d50e-120">パッケージを実行せずに、列のみを含む空の RAW ファイル (メタデータのみのファイル) を生成するには、このボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d50e-120">Click the button to generate an empty raw file that contains only the columns (metadata-only file), without having to run the package.</span></span> <span data-ttu-id="0d50e-121">ファイルには、 **[RAW ファイル変換先エディター]** の **[列]** ページで選択した列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0d50e-121">The file contains the columns that you selected on the **Columns** page of the **Raw File Destination Editor**.</span></span> <span data-ttu-id="0d50e-122">RAW ファイル ソースの参照先を、このメタデータのみのファイルにすることができます。</span><span class="sxs-lookup"><span data-stu-id="0d50e-122">You can point the Raw File source to this metadata-only file.</span></span>  
  
 <span data-ttu-id="0d50e-123">**[初期 RAW ファイルの生成]** をクリックすると、メッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0d50e-123">When you click **Generate initial raw file**, a message box appears.</span></span> <span data-ttu-id="0d50e-124">ファイルの作成を続行するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d50e-124">Click **OK** to proceed with creating the file.</span></span> <span data-ttu-id="0d50e-125">**[列]** ページで別の列の一覧を選択するには、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d50e-125">Click **Cancel** to select a different list of columns on the **Columns** page.</span></span>  
  
##  <a name="set-options-on-the-columns-tab"></a><a name="mapping"></a><span data-ttu-id="0d50e-126">[列] タブのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="0d50e-126">Set options on the Columns tab</span></span>  
 <span data-ttu-id="0d50e-127">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="0d50e-127">**Available Input Columns**</span></span>  
 <span data-ttu-id="0d50e-128">RAW ファイルに書き込む 1 つ以上の入力列を選択します。</span><span class="sxs-lookup"><span data-stu-id="0d50e-128">Select one or more input columns to write to the raw file.</span></span>  
  
 <span data-ttu-id="0d50e-129">**入力列**</span><span class="sxs-lookup"><span data-stu-id="0d50e-129">**Input Column**</span></span>  
 <span data-ttu-id="0d50e-130">**[使用できる入力列]** から選択した場合、このテーブルに入力列が自動的に追加されます。入力列をこのテーブルで直接選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="0d50e-130">An input column is automatically added to this table when you select it under **Available Input Columns**, or you can select the input column directly in this table.</span></span>  
  
 <span data-ttu-id="0d50e-131">**[出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="0d50e-131">**Output Alias**</span></span>  
 <span data-ttu-id="0d50e-132">出力列に使用する代替名を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d50e-132">Specify an alternate name to use for the output column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d50e-133">参照</span><span class="sxs-lookup"><span data-stu-id="0d50e-133">See Also</span></span>  
 [<span data-ttu-id="0d50e-134">RAW ファイル変換先</span><span class="sxs-lookup"><span data-stu-id="0d50e-134">Raw File Destination</span></span>](data-flow/raw-file-destination.md)  
  
  
