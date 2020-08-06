---
title: チェックインされたファイルの編集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying checked-in files
- checking in files
ms.assetid: 560cd19f-ab22-4273-b00c-149993a630e6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e2dbe1aad203dfdc83e438d5b7f4ed19c15038c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716638"
---
# <a name="edit-checked-in-files"></a><span data-ttu-id="5c442-102">チェックインされているファイルの編集</span><span class="sxs-lookup"><span data-stu-id="5c442-102">Edit Checked-In Files</span></span>
  <span data-ttu-id="5c442-103">通常、ソース管理の対象であるファイルは、チェックアウトしてから編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c442-103">You typically must check out source-controlled files before you can edit them.</span></span> <span data-ttu-id="5c442-104">ただし、を構成して、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] チェックアウトしていないファイルを変更できるようにすることができます。これを行うと、ファイルを保存するまで、変更はメモリに保持されます。</span><span class="sxs-lookup"><span data-stu-id="5c442-104">However, you can configure [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] so that you can modify files you have not checked out. When doing so, your changes are held in memory until you save the files.</span></span> <span data-ttu-id="5c442-105">ファイルの保存時に、ファイルをソース管理からチェックアウトするよう求められます。</span><span class="sxs-lookup"><span data-stu-id="5c442-105">You will then be prompted to check out the file from source control.</span></span>  
  
 <span data-ttu-id="5c442-106">チームで作業している場合、ソース管理プロバイダーがローカル バージョンとサーバー バージョンの両方のチェックアウトをサポートしていない限り、チェックインされているファイルの編集は許可しないでください。</span><span class="sxs-lookup"><span data-stu-id="5c442-106">If you work on a team, allowing checked-in files to be edited is not recommended unless your source control provider supports both local version and server version checkouts.</span></span> <span data-ttu-id="5c442-107">ほとんどのプロバイダーはローカル バージョンのチェックアウトをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5c442-107">Most providers do not support local version checkouts.</span></span> <span data-ttu-id="5c442-108">プロバイダーがローカル バージョンのチェックアウトをサポートしていない場合、チェックインされているファイルを編集するときは、ファイルをチェックインする前にメモリ内のバージョンとサーバーのバージョンを手動でマージする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c442-108">If your provider does not support local version checkouts and you edit a checked-in file, you have to merge the in-memory and server versions manually before the file can be checked in.</span></span> <span data-ttu-id="5c442-109">この状況では、自動マージとプロバイダーが補助するマージはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="5c442-109">Automatic and provider-assisted merges are unsupported in this situation.</span></span>  
  
### <a name="to-edit-checked-in-files"></a><span data-ttu-id="5c442-110">チェックインされているファイルを編集するには</span><span class="sxs-lookup"><span data-stu-id="5c442-110">To edit checked-in files</span></span>  
  
1.  <span data-ttu-id="5c442-111">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c442-111">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="5c442-112">[**オプション**] ダイアログボックスで、[**ソース**] フォルダーを展開し、[**環境**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c442-112">In the **Options** dialog box, expand the **Source Contro**l folder, and then click **Environment**.</span></span>  
  
3.  <span data-ttu-id="5c442-113">[**チェックインされた項目の編集を許可する**] をクリックし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c442-113">Click **Allow checked-in items to be edited**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c442-114">参照</span><span class="sxs-lookup"><span data-stu-id="5c442-114">See Also</span></span>  
 <span data-ttu-id="5c442-115">[チェックインの管理](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="5c442-115">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="5c442-116">チェックアウトの管理</span><span class="sxs-lookup"><span data-stu-id="5c442-116">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
