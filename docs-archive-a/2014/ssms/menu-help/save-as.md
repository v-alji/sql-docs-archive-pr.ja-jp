---
title: '[名前を付けて保存] | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vs.saveas
helpviewer_keywords:
- Save As dialog box
ms.assetid: 61347757-f5a3-481d-8b05-1fed086629b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: e47d9c37371283fc6fba2754896d77b51d26cef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645962"
---
# <a name="save-as"></a><span data-ttu-id="63258-102">[名前を付けて保存]</span><span class="sxs-lookup"><span data-stu-id="63258-102">Save As</span></span>
  <span data-ttu-id="63258-103">このダイアログ ボックスを使用すると、現在のアイテムのインスタンスを、指定した場所に指定したファイル形式で保存できます。</span><span class="sxs-lookup"><span data-stu-id="63258-103">Use this dialog box to save an instance of the current item at a specified location in a specified file format.</span></span> <span data-ttu-id="63258-104">このダイアログボックスを表示するには、[ファイル] メニューの [名前を付けて**保存**] をクリックする *\<file>* **As**か ( **File** *\<file>* は現在の項目の名前)、コードエディターで ALT キーを押しながら F キーを押します。</span><span class="sxs-lookup"><span data-stu-id="63258-104">To display this dialog box, click **Save** *\<file>* **As** on the **File** menu (where *\<file>* is the name of the current item), or press ALT+F, A in the Code Editor.</span></span>  
  
## <a name="central-panel"></a><span data-ttu-id="63258-105">中央のパネル</span><span class="sxs-lookup"><span data-stu-id="63258-105">Central Panel</span></span>  
 <span data-ttu-id="63258-106">**[保存先]**</span><span class="sxs-lookup"><span data-stu-id="63258-106">**Save in**</span></span>  
 <span data-ttu-id="63258-107">このドロップダウン メニューから、既存のプロジェクト フォルダーを探します。</span><span class="sxs-lookup"><span data-stu-id="63258-107">Locate the existing project folder from this drop-down menu.</span></span> <span data-ttu-id="63258-108">この一覧でフォルダーを選択すると、そのフォルダーの内容が下の主要ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="63258-108">Selecting a folder from this list displays the contents of the folder in the primary pane below.</span></span>  
  
 <span data-ttu-id="63258-109">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="63258-109">**File name**</span></span>  
 <span data-ttu-id="63258-110">このオプションを使用して、現在のファイル名の表示、ファイル名の変更、表示されるファイルとフォルダーのフィルター選択を行います。</span><span class="sxs-lookup"><span data-stu-id="63258-110">Use this option to view the current file name, change the file name, or filter the files and folders that are displayed.</span></span> <span data-ttu-id="63258-111">表示されるファイルとフォルダーをフィルター選択するには、フィルターの対象となるファイル名またはファイル名の一部を入力します。</span><span class="sxs-lookup"><span data-stu-id="63258-111">To filter the files and folders that are displayed, enter a full or partial file name on which to filter.</span></span> <span data-ttu-id="63258-112">ワイルドカードとしてアスタリスク (`*`) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="63258-112">You can use the asterisk (`*`) as a wildcard.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="63258-113">Web およびネットワークの場所にあるファイルを表示するには、 **[ファイル名]** ボックスに URL またはネットワーク パスを入力します。</span><span class="sxs-lookup"><span data-stu-id="63258-113">To display files on Web and network locations, enter a URL or network path in the **File name** box.</span></span> <span data-ttu-id="63258-114">たとえば、「 <http://mywebsite> 」と入力した場合は、"mywebsite" という Web の場所で利用可能なファイルが表示され、「\\\myserver\myshare」と入力した場合は、"myserver" の "myshare" という場所で利用可能なファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="63258-114">For example, "<http://mywebsite>" displays the files available at the "mywebsite" Web location and "\\\myserver\myshare" displays the files available at the "myshare" location on "myserver".</span></span>  
  
 <span data-ttu-id="63258-115">**ファイルの種類**</span><span class="sxs-lookup"><span data-stu-id="63258-115">**Save as type**</span></span>  
 <span data-ttu-id="63258-116">このオプションを使用して、選択したアイテムに適用する新しいファイルの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="63258-116">Use this option to select a new file type for the selected item.</span></span> <span data-ttu-id="63258-117">選択したアイテムに適用できるすべてのファイル タイプが表示されます。</span><span class="sxs-lookup"><span data-stu-id="63258-117">The file types displayed include all available file types to which the selected item can be converted.</span></span>  
  
 <span data-ttu-id="63258-118">**[保存オプションの詳細設定]**</span><span class="sxs-lookup"><span data-stu-id="63258-118">**Advanced Save Options**</span></span>  
 <span data-ttu-id="63258-119">**[保存オプションの詳細設定]** ダイアログ ボックスを開くには、 **[保存]** ボタンの右側にある小さな三角形をクリックして **[エンコード付きで保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63258-119">To access the **Advanced Save Options Dialog Box**, select the small rectangle at the right of the **Save** button and then click **Save with Encoding**.</span></span> <span data-ttu-id="63258-120">このダイアログ ボックスを使用して、ファイルのエンコードと行末に使用する文字を指定します。</span><span class="sxs-lookup"><span data-stu-id="63258-120">Use this dialog box to specify an encoding for the file and the characters to use at Line endings.</span></span>  
  
## <a name="left-panel"></a><span data-ttu-id="63258-121">左側のパネル</span><span class="sxs-lookup"><span data-stu-id="63258-121">Left Panel</span></span>  
 <span data-ttu-id="63258-122">**[デスクトップ]**</span><span class="sxs-lookup"><span data-stu-id="63258-122">**Desktop**</span></span>  
 <span data-ttu-id="63258-123">デスクトップに置かれているファイルとフォルダーをすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="63258-123">Displays any files and folders located on the desktop.</span></span>  
  
 <span data-ttu-id="63258-124">**[マイ プロジェクト]**</span><span class="sxs-lookup"><span data-stu-id="63258-124">**My Projects**</span></span>  
 <span data-ttu-id="63258-125">**[マイ プロジェクト]** または最後に開いた場所にあるファイルとフォルダーを表示します。</span><span class="sxs-lookup"><span data-stu-id="63258-125">Displays files and folders at the **My Projects** or the most recently visited location.</span></span>  
  
 <span data-ttu-id="63258-126">**[マイ コンピューター]**</span><span class="sxs-lookup"><span data-stu-id="63258-126">**My Computer**</span></span>  
 <span data-ttu-id="63258-127">コンピューターの **[マイ コンピューター]** を表示します。</span><span class="sxs-lookup"><span data-stu-id="63258-127">Displays the **My Computer** location on your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63258-128">参照</span><span class="sxs-lookup"><span data-stu-id="63258-128">See Also</span></span>  
 <span data-ttu-id="63258-129">[保存オプションの詳細設定](advanced-save-options.md) </span><span class="sxs-lookup"><span data-stu-id="63258-129">[Advanced Save Options](advanced-save-options.md) </span></span>  
 [<span data-ttu-id="63258-130">エンコーディングによるファイルの管理</span><span class="sxs-lookup"><span data-stu-id="63258-130">Manage Files with Encoding</span></span>](../solution/manage-files-with-encoding.md)  
  
  
