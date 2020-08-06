---
title: '[ファイル接続マネージャーの追加] ダイアログ ボックスの UI リファレンス | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileconnection.f1
helpviewer_keywords:
- Add File Connection Manager
ms.assetid: 9370bfb5-5993-4ad8-a9cd-2de53f320f34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 044d8e2eaae9db17d7155cb354f8d009750f44d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738580"
---
# <a name="add-file-connection-manager-dialog-box-ui-reference"></a><span data-ttu-id="0f001-102">[ファイル接続マネージャーの追加] ダイアログ ボックスの UI リファレンス</span><span class="sxs-lookup"><span data-stu-id="0f001-102">Add File Connection Manager Dialog Box UI Reference</span></span>
  <span data-ttu-id="0f001-103">**[ファイル接続マネージャーの追加]** ダイアログ ボックスを使用すると、ファイルまたはフォルダーのグループへの接続を定義できます。</span><span class="sxs-lookup"><span data-stu-id="0f001-103">Use the **Add File Connection Manager** dialog box to define a connection to a group of files or folders.</span></span>  
  
 <span data-ttu-id="0f001-104">複数のファイルの接続マネージャーの詳細については、「 [Multiple Files Connection Manager](multiple-files-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f001-104">To learn more about the Multiple Files connection manager, see [Multiple Files Connection Manager](multiple-files-connection-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f001-105">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の組み込みタスクとデータ フロー コンポーネントは、複数ファイル接続マネージャーを使用しません。</span><span class="sxs-lookup"><span data-stu-id="0f001-105">The built-in tasks and data flow components in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] do not use the Multiple Files connection manager.</span></span> <span data-ttu-id="0f001-106">ただし、スクリプト タスクまたはスクリプト コンポーネントでは、この接続マネージャーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0f001-106">However, you can use this connection manager in the Script task or Script component.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0f001-107">オプション</span><span class="sxs-lookup"><span data-stu-id="0f001-107">Options</span></span>  
 <span data-ttu-id="0f001-108">**[使用法の種類]**</span><span class="sxs-lookup"><span data-stu-id="0f001-108">**Usage type**</span></span>  
 <span data-ttu-id="0f001-109">複数のファイルの接続マネージャーに使用するファイルの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="0f001-109">Specify the type of files to use for the multiple files connection manager.</span></span>  
  
|<span data-ttu-id="0f001-110">値</span><span class="sxs-lookup"><span data-stu-id="0f001-110">Value</span></span>|<span data-ttu-id="0f001-111">説明</span><span class="sxs-lookup"><span data-stu-id="0f001-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0f001-112">**[ファイルの作成]**</span><span class="sxs-lookup"><span data-stu-id="0f001-112">**Create files**</span></span>|<span data-ttu-id="0f001-113">接続マネージャーはファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="0f001-113">The connection manager will create the files.</span></span>|  
|<span data-ttu-id="0f001-114">**[既存のファイル]**</span><span class="sxs-lookup"><span data-stu-id="0f001-114">**Existing files**</span></span>|<span data-ttu-id="0f001-115">接続マネージャーは既存のファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="0f001-115">The connection manager will use existing files.</span></span>|  
|<span data-ttu-id="0f001-116">**[フォルダーの作成]**</span><span class="sxs-lookup"><span data-stu-id="0f001-116">**Create folders**</span></span>|<span data-ttu-id="0f001-117">接続マネージャーはフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0f001-117">The connection manager will create the folders.</span></span>|  
|<span data-ttu-id="0f001-118">**[既存のフォルダー]**</span><span class="sxs-lookup"><span data-stu-id="0f001-118">**Existing folders**</span></span>|<span data-ttu-id="0f001-119">接続マネージャーは既存のフォルダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="0f001-119">The connection manager will use existing folders.</span></span>|  
  
 <span data-ttu-id="0f001-120">**[ファイルまたはフォルダー]**</span><span class="sxs-lookup"><span data-stu-id="0f001-120">**Files / Folders**</span></span>  
 <span data-ttu-id="0f001-121">次のボタンを使用して追加したファイルまたはフォルダーを表示します。</span><span class="sxs-lookup"><span data-stu-id="0f001-121">View the files or folders that you have added by using the buttons described as follows.</span></span>  
  
 <span data-ttu-id="0f001-122">**追加**</span><span class="sxs-lookup"><span data-stu-id="0f001-122">**Add**</span></span>  
 <span data-ttu-id="0f001-123">**[ファイルの選択]** ダイアログ ボックスを使用してファイルを追加するか、 **[フォルダーの参照]** ダイアログ ボックスを使用してフォルダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="0f001-123">Add a file by using the **Select Files** dialog box, or add a folder by using the **Browse for Folder** dialog box.</span></span>  
  
 <span data-ttu-id="0f001-124">**[編集]**</span><span class="sxs-lookup"><span data-stu-id="0f001-124">**Edit**</span></span>  
 <span data-ttu-id="0f001-125">ファイルまたはフォルダーを選択し、 **[ファイルの選択]** または **[フォルダーの参照]** ダイアログ ボックスを使用して別のファイルまたはフォルダーで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0f001-125">Select a file or folder, and then replace it with a different file or folder by using the **Select Files** or **Browse for Folder** dialog box.</span></span>  
  
 <span data-ttu-id="0f001-126">**Remove**</span><span class="sxs-lookup"><span data-stu-id="0f001-126">**Remove**</span></span>  
 <span data-ttu-id="0f001-127">ファイルまたはフォルダーを選択し、 **[削除]** ボタンを使用して一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="0f001-127">Select a file or folder, and then remove it from the list by using the **Remove** button.</span></span>  
  
 <span data-ttu-id="0f001-128">**矢印ボタン**</span><span class="sxs-lookup"><span data-stu-id="0f001-128">**Arrow buttons**</span></span>  
 <span data-ttu-id="0f001-129">ファイルまたはフォルダーを選択し、矢印ボタンを使用して上または下に移動して、アクセスのシーケンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="0f001-129">Select a file or folder, and then use the arrow buttons to move it up or down to specify the sequence of access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f001-130">参照</span><span class="sxs-lookup"><span data-stu-id="0f001-130">See Also</span></span>  
 [<span data-ttu-id="0f001-131">Integration Services のエラーとメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="0f001-131">Integration Services Error and Message Reference</span></span>](../integration-services-error-and-message-reference.md)  
  
  
