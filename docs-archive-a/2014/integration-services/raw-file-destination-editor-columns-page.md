---
title: '[Raw ファイル変換先エディター] ([列] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledestinationcolumns.f1
ms.assetid: 37f61d0b-1269-42ee-94ab-011cbaac63e9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a89d8ca46805a23fd03465ed40428081499dccb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713274"
---
# <a name="raw-file-destination-editor-columns-page"></a><span data-ttu-id="e2faa-102">[Raw ファイル変換先エディター] ([列] ページ)</span><span class="sxs-lookup"><span data-stu-id="e2faa-102">Raw File Destination Editor (Columns Page)</span></span>
  <span data-ttu-id="e2faa-103">ファイルに RAW データを書き込むための RAW ファイル変換先を構成するには、RAW ファイル変換先エディターを使用します。</span><span class="sxs-lookup"><span data-stu-id="e2faa-103">Use the Raw File Destination Editor to configure the Raw File destination to write raw data to a file.</span></span>  
  
 <span data-ttu-id="e2faa-104">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="e2faa-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="e2faa-105">Raw ファイル変換先エディターを開く</span><span class="sxs-lookup"><span data-stu-id="e2faa-105">Open the Raw File Destination Editor</span></span>](#open)  
  
-   <span data-ttu-id="e2faa-106">[[接続マネージャー] タブのオプションの設定](#connection)</span><span class="sxs-lookup"><span data-stu-id="e2faa-106">[Set options on the Connection Manager tab](#connection)</span></span>  
  
-   <span data-ttu-id="e2faa-107">[[列] タブのオプションの設定](#mapping)</span><span class="sxs-lookup"><span data-stu-id="e2faa-107">[Set options on the Columns tab](#mapping)</span></span>  
  
##  <a name="open-the-raw-file-destination-editor"></a><a name="open"></a> <span data-ttu-id="e2faa-108">RAW ファイル変換先エディターを開く</span><span class="sxs-lookup"><span data-stu-id="e2faa-108">Open the Raw File Destination Editor</span></span>  
  
1.  <span data-ttu-id="e2faa-109">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]パッケージに RAW ファイル変換先を追加します。</span><span class="sxs-lookup"><span data-stu-id="e2faa-109">Add the Raw File destination to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="e2faa-110">コンポーネントを右クリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e2faa-110">Right-click the component and then click **Edit**.</span></span>  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> <span data-ttu-id="e2faa-111">[接続マネージャー] タブのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="e2faa-111">Set options on the Connection Manager tab</span></span>  
 <span data-ttu-id="e2faa-112">**アクセス モード**</span><span class="sxs-lookup"><span data-stu-id="e2faa-112">**Access mode**</span></span>  
 <span data-ttu-id="e2faa-113">ファイル名の指定方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="e2faa-113">Select how the file name is specified.</span></span> <span data-ttu-id="e2faa-114">ファイル名とパスを直接入力するには **[ファイル名]** を選択します。ファイル名を含んでいる変数を指定するには、 **[変数からのファイル名]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e2faa-114">Select **File name** to enter the file name and path directly, of **File name from variable** to specify a variable that contains the file name.</span></span>  
  
 <span data-ttu-id="e2faa-115">**[ファイル名]** または **[変数名]**</span><span class="sxs-lookup"><span data-stu-id="e2faa-115">**File name** or **Variable name**</span></span>  
 <span data-ttu-id="e2faa-116">RAW ファイルの名前とパスを入力するか、またはファイル名を含んでいる変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="e2faa-116">Enter the name and path of the raw file, or select the variable that contains the file name.</span></span>  
  
 <span data-ttu-id="e2faa-117">**[書き込みオプション]**</span><span class="sxs-lookup"><span data-stu-id="e2faa-117">**Write option**</span></span>  
 <span data-ttu-id="e2faa-118">ファイルの作成およびファイルへの書き込みに使用するメソッドを選択します。</span><span class="sxs-lookup"><span data-stu-id="e2faa-118">Select the method used to create and write to the file.</span></span>  
  
 <span data-ttu-id="e2faa-119">**[初期 RAW ファイルの生成]**</span><span class="sxs-lookup"><span data-stu-id="e2faa-119">**Generate initial raw file**</span></span>  
 <span data-ttu-id="e2faa-120">パッケージを実行せずに、列のみを含む空の RAW ファイル (メタデータのみのファイル) を生成するには、このボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e2faa-120">Click the button to generate an empty raw file that contains only the columns (metadata-only file), without having to run the package.</span></span> <span data-ttu-id="e2faa-121">RAW ファイル ソースの参照先を、メタデータのみのファイルにすることができます。</span><span class="sxs-lookup"><span data-stu-id="e2faa-121">You can point the Raw File source to the metadata-only file.</span></span>  
  
 <span data-ttu-id="e2faa-122">このボタンをクリックすると、列の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e2faa-122">When you click the button, a list of the columns appears.</span></span> <span data-ttu-id="e2faa-123">[キャンセル] をクリックして列を変更するか、[OK] をクリックしてファイルの作成を続行することができます。</span><span class="sxs-lookup"><span data-stu-id="e2faa-123">You can click cancel and modify the columns or click OK to proceed with creating the file.</span></span>  
  
##  <a name="set-options-on-the-columns-tab"></a><a name="mapping"></a><span data-ttu-id="e2faa-124">[列] タブのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="e2faa-124">Set options on the Columns tab</span></span>  
 <span data-ttu-id="e2faa-125">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="e2faa-125">**Available Input Columns**</span></span>  
 <span data-ttu-id="e2faa-126">RAW ファイルに書き込む 1 つ以上の入力列を選択します。</span><span class="sxs-lookup"><span data-stu-id="e2faa-126">Select one or more input columns to write to the raw file.</span></span>  
  
 <span data-ttu-id="e2faa-127">**入力列**</span><span class="sxs-lookup"><span data-stu-id="e2faa-127">**Input Column**</span></span>  
 <span data-ttu-id="e2faa-128">**[使用できる入力列]** から選択した場合、このテーブルに入力列が自動的に追加されます。入力列をこのテーブルで直接選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="e2faa-128">An input column is automatically added to this table when you select it under **Available Input Columns**, or you can select the input column directly in this table.</span></span>  
  
 <span data-ttu-id="e2faa-129">**[出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="e2faa-129">**Output Alias**</span></span>  
 <span data-ttu-id="e2faa-130">出力列に使用する代替名を指定します。</span><span class="sxs-lookup"><span data-stu-id="e2faa-130">Specify an alternate name to use for the output column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2faa-131">参照</span><span class="sxs-lookup"><span data-stu-id="e2faa-131">See Also</span></span>  
 [<span data-ttu-id="e2faa-132">RAW ファイル変換先</span><span class="sxs-lookup"><span data-stu-id="e2faa-132">Raw File Destination</span></span>](data-flow/raw-file-destination.md)  
  
  
