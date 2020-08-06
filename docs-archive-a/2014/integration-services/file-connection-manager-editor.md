---
title: ファイル接続マネージャーエディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileconnectionmanager.f1
helpviewer_keywords:
- File Connection Manager Editor
ms.assetid: 051c48e5-3d86-49af-b554-ff62e3de3622
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2f3261b836d4800787fc078b05b15e469d3c200d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644021"
---
# <a name="file-connection-manager-editor"></a><span data-ttu-id="7f710-102">[ファイル接続マネージャー エディター] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="7f710-102">File Connection Manager Editor</span></span>
  <span data-ttu-id="7f710-103">**[ファイル接続マネージャー エディター]** ダイアログ ボックスを使用すると、ファイルまたはフォルダーに接続するためのプロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7f710-103">Use the **File Connection Manager Editor** dialog box to specify the properties used to connect to a file or a folder.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f710-104">ファイル接続マネージャーの ConnectionString プロパティは、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の [プロパティ] ウィンドウで式を指定することで設定できます。</span><span class="sxs-lookup"><span data-stu-id="7f710-104">You can set the ConnectionString property for the File connection manager by specifying an expression in the Properties window of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="7f710-105">ただし、式を使用してファイルまたはフォルダーを指定するときに検証エラーが発生しないようにするには、[ファイル**接続マネージャーエディター**] の [ファイル **/フォルダー**] で、ファイルまたはフォルダーのパスを追加します。</span><span class="sxs-lookup"><span data-stu-id="7f710-105">However, to avoid a validation error when you use an expression to specify the file or folder, in the **File Connection Manager Editor**, for **File/Folder**, add a file or folder path.</span></span>  
  
 <span data-ttu-id="7f710-106">ファイル接続マネージャーの詳細については、「 [File Connection Manager](connection-manager/file-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f710-106">To learn more about the File connection manager, see [File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7f710-107">Options</span><span class="sxs-lookup"><span data-stu-id="7f710-107">Options</span></span>  
 <span data-ttu-id="7f710-108">**[使用法の種類]**</span><span class="sxs-lookup"><span data-stu-id="7f710-108">**Usage Type**</span></span>  
 <span data-ttu-id="7f710-109">**ファイル接続マネージャー** が既存のファイルまたはフォルダーに接続するか、新しいファイルまたはフォルダーを作成するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7f710-109">Specify whether the **File Connection Manager** connects to an existing file or folder or creates a new file or folder.</span></span>  
  
|<span data-ttu-id="7f710-110">値</span><span class="sxs-lookup"><span data-stu-id="7f710-110">Value</span></span>|<span data-ttu-id="7f710-111">説明</span><span class="sxs-lookup"><span data-stu-id="7f710-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7f710-112">[ファイルの作成]</span><span class="sxs-lookup"><span data-stu-id="7f710-112">Create file</span></span>|<span data-ttu-id="7f710-113">実行時に新しいファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7f710-113">Create a new file at run time.</span></span>|  
|<span data-ttu-id="7f710-114">[既存のファイル]</span><span class="sxs-lookup"><span data-stu-id="7f710-114">Existing file</span></span>|<span data-ttu-id="7f710-115">既存のファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="7f710-115">Use an existing file.</span></span>|  
|<span data-ttu-id="7f710-116">フォルダーの作成</span><span class="sxs-lookup"><span data-stu-id="7f710-116">Create folder</span></span>|<span data-ttu-id="7f710-117">実行時に新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="7f710-117">Create a new folder at run time.</span></span>|  
|<span data-ttu-id="7f710-118">[既存のフォルダー]</span><span class="sxs-lookup"><span data-stu-id="7f710-118">Existing folder</span></span>|<span data-ttu-id="7f710-119">既存のフォルダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="7f710-119">Use an existing folder.</span></span>|  
  
 <span data-ttu-id="7f710-120">**[ファイル]/[フォルダー]**</span><span class="sxs-lookup"><span data-stu-id="7f710-120">**File / Folder**</span></span>  
 <span data-ttu-id="7f710-121">**[ファイル]** の場合は、使用するファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7f710-121">If **File**, specify the file to use.</span></span>  
  
 <span data-ttu-id="7f710-122">**[フォルダー]** の場合は、使用するファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7f710-122">If **Folder**, specify the folder to use.</span></span>  
  
 <span data-ttu-id="7f710-123">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="7f710-123">**Browse**</span></span>  
 <span data-ttu-id="7f710-124">**[ファイルの選択]** ダイアログ ボックスまたは **[フォルダーの参照]** ダイアログ ボックスを使用して、ファイルまたはフォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="7f710-124">Select the file or folder by using the **Select File** or **Browse for Folder** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f710-125">参照</span><span class="sxs-lookup"><span data-stu-id="7f710-125">See Also</span></span>  
 [<span data-ttu-id="7f710-126">Integration Services のエラーおよびメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="7f710-126">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
