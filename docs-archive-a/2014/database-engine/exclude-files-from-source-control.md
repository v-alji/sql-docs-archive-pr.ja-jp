---
title: ソース管理からファイルを除外する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- excluding files from source control
- source controls [SQL Server Management Studio], file exclusions
ms.assetid: 7dcb6514-db5c-49eb-8b5a-2c766ce39aa7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9fb3c5ccb4fcaad062236eec6d04f995557dc2b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716621"
---
# <a name="exclude-files-from-source-control"></a><span data-ttu-id="59abd-102">ソース管理からのファイルの除外</span><span class="sxs-lookup"><span data-stu-id="59abd-102">Exclude Files from Source Control</span></span>
  <span data-ttu-id="59abd-103">作業中のソリューションにソース管理サービスを必要としないファイルが含まれている場合は、[**ソース管理から除外**する] コマンドを使用して、ソース管理からファイルを除外できます。</span><span class="sxs-lookup"><span data-stu-id="59abd-103">If the solution you are working on contains files that do not require source control services, you can use the **Exclude from Source Control** command to exclude the file from source control.</span></span> <span data-ttu-id="59abd-104">ファイルを除外すると、そのファイルは [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe データベースに残りますが、プロジェクトと共にチェックインまたはチェックアウトされなくなります。</span><span class="sxs-lookup"><span data-stu-id="59abd-104">When you do this, the file remains in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe database, but it is no longer checked in or out with the project.</span></span>  
  
 <span data-ttu-id="59abd-105">[**ソース管理から除外**する] コマンドは、生成されたファイルに対してのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="59abd-105">You should use the **Exclude from Source Control** command only on generated files.</span></span> <span data-ttu-id="59abd-106">生成されたファイルは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ソリューション内の別のファイルの内容に基づいて、によって完全に再作成できるファイルです。</span><span class="sxs-lookup"><span data-stu-id="59abd-106">A generated file is one that can be entirely re-created by [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] based on the contents of another file in the solution.</span></span>  
  
### <a name="to-exclude-a-file-from-source-control"></a><span data-ttu-id="59abd-107">ソース管理からファイルを除外するには</span><span class="sxs-lookup"><span data-stu-id="59abd-107">To exclude a file from source control</span></span>  
  
1.  <span data-ttu-id="59abd-108">ソリューション エクスプローラーで、除外するファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="59abd-108">In Solution Explorer, select the file to exclude.</span></span>  
  
2.  <span data-ttu-id="59abd-109">[**ファイル**] メニューの [**ソース管理**] をポイントし、[ **Exclude** *\<file name>* **ソース管理から**除外] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59abd-109">On the **File** menu, point to **Source Control**, and then click **Exclude** *\<file name>* **from Source Control**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59abd-110">参照</span><span class="sxs-lookup"><span data-stu-id="59abd-110">See Also</span></span>  
 <span data-ttu-id="59abd-111">[ソース管理の基礎](../../2014/database-engine/source-control-basics.md) </span><span class="sxs-lookup"><span data-stu-id="59abd-111">[Source Control Basics](../../2014/database-engine/source-control-basics.md) </span></span>  
 <span data-ttu-id="59abd-112">[ソース管理オプションの設定](../../2014/database-engine/set-source-control-options.md) </span><span class="sxs-lookup"><span data-stu-id="59abd-112">[Set Source Control Options](../../2014/database-engine/set-source-control-options.md) </span></span>  
 [<span data-ttu-id="59abd-113">ソース管理接続の変更</span><span class="sxs-lookup"><span data-stu-id="59abd-113">Change Source Control Connections</span></span>](../../2014/database-engine/change-source-control-connections.md)  
  
  
