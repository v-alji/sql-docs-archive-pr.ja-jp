---
title: ファイルの比較 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- versions [SQL Server], file comparisons
- comparing files
- file comparisons [SQL Server]
ms.assetid: 728811c4-5d7a-4420-abce-f56c5a0994d2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f29bf7098f0c73d0b672e20b973b1347349b31f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642320"
---
# <a name="compare-files"></a><span data-ttu-id="7a6e0-102">ファイルの比較</span><span class="sxs-lookup"><span data-stu-id="7a6e0-102">Compare Files</span></span>
  <span data-ttu-id="7a6e0-103">ファイルを比較して、ファイルがどのような過程で現在の状態になったのかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7a6e0-103">You can compare files to determine how a file has progressed to its present state.</span></span> <span data-ttu-id="7a6e0-104">たとえば、ソース ファイルのバージョンをチェックインした後に、コード プロジェクトのビルドで不具合を発見した場合、現在のファイル バージョンと以前のファイル バージョンを比較できます。</span><span class="sxs-lookup"><span data-stu-id="7a6e0-104">For example, if you detect a defect in a build of your code project after a particular source file version is checked in, you can compare the current file version to a previous one.</span></span> <span data-ttu-id="7a6e0-105">そうすれば、不具合を引き起こしたコードの位置を正確に検出できます。</span><span class="sxs-lookup"><span data-stu-id="7a6e0-105">This helps you to pinpoint the code that introduced the defect.</span></span>  
  
 <span data-ttu-id="7a6e0-106">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して、プロジェクトまたはファイルのローカル コピーと、ソース管理に格納されているバージョンを比較できます。2 つのローカル ファイルを比較することもできます。</span><span class="sxs-lookup"><span data-stu-id="7a6e0-106">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to compare a local copy of a project or file to the version stored in source control, or to compare two local files.</span></span> <span data-ttu-id="7a6e0-107">また、 **History**コマンドを使用すると、ソース管理されている2つのバージョンを比較できます。</span><span class="sxs-lookup"><span data-stu-id="7a6e0-107">Also, using the **History** command, you can compare any two source-controlled versions.</span></span>  
  
### <a name="to-compare-files"></a><span data-ttu-id="7a6e0-108">ファイルを比較するには</span><span class="sxs-lookup"><span data-stu-id="7a6e0-108">To compare files</span></span>  
  
1.  <span data-ttu-id="7a6e0-109">ソリューション エクスプローラーで、プロジェクトまたはプロジェクト ファイルの 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="7a6e0-109">In Solution Explorer, select either a project or one of the project files.</span></span>  
  
2.  <span data-ttu-id="7a6e0-110">[**ファイル**] メニューの [**ソース管理**] をポイントし、[**比較**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a6e0-110">On the **File** menu, point to **Source Control**, and click **Compare**.</span></span>  
  
3.  <span data-ttu-id="7a6e0-111">[**相違点オプション**] ダイアログボックスで、適切なオプションを選択し、[**レポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a6e0-111">In the **Difference Options** dialog box, select the appropriate options, and then click **Report**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a6e0-112">参照</span><span class="sxs-lookup"><span data-stu-id="7a6e0-112">See Also</span></span>  
 <span data-ttu-id="7a6e0-113">[バージョン情報の設定と取得](../../2014/database-engine/set-and-retrieve-version-information.md) </span><span class="sxs-lookup"><span data-stu-id="7a6e0-113">[Set and Retrieve Version Information](../../2014/database-engine/set-and-retrieve-version-information.md) </span></span>  
 <span data-ttu-id="7a6e0-114">[ファイル履歴の表示](../../2014/database-engine/view-file-history.md) </span><span class="sxs-lookup"><span data-stu-id="7a6e0-114">[View File History](../../2014/database-engine/view-file-history.md) </span></span>  
 <span data-ttu-id="7a6e0-115">[プロジェクト履歴の表示](../../2014/database-engine/view-project-history.md) </span><span class="sxs-lookup"><span data-stu-id="7a6e0-115">[View Project History](../../2014/database-engine/view-project-history.md) </span></span>  
 <span data-ttu-id="7a6e0-116">[ファイルの状態の表示](../../2014/database-engine/view-file-status.md) </span><span class="sxs-lookup"><span data-stu-id="7a6e0-116">[View File Status](../../2014/database-engine/view-file-status.md) </span></span>  
 [<span data-ttu-id="7a6e0-117">ファイルの取得</span><span class="sxs-lookup"><span data-stu-id="7a6e0-117">Retrieve Files</span></span>](../../2014/database-engine/retrieve-files.md)  
  
  
