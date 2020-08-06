---
title: ソース管理からソリューションを開く |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- opening solutions
- solutions [SQL Server Management Studio], opening
ms.assetid: a96a1f0d-0183-4587-a3b0-4598309cbdd2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 808a4851bcc1f51690b2ba924a859bcccf9a6adb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644612"
---
# <a name="open-solutions-from-source-control"></a><span data-ttu-id="0b317-102">ソース管理からソリューションを開く</span><span class="sxs-lookup"><span data-stu-id="0b317-102">Open Solutions from Source Control</span></span>
  <span data-ttu-id="0b317-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して、ソース管理からソリューションを直接開くことができます。</span><span class="sxs-lookup"><span data-stu-id="0b317-103">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to open solutions directly from source control.</span></span> <span data-ttu-id="0b317-104">直接ソリューションを開く場合は、Studio 環境によって、ソリューション ファイルの最新バージョンのコピーが指定した場所に作成されます。</span><span class="sxs-lookup"><span data-stu-id="0b317-104">When you do this, the Studio environment creates a copy of the latest version of the solution files at the location you specify.</span></span>  
  
 <span data-ttu-id="0b317-105">ソリューションのローカル コピーがローカル ディスクに存在しない場合は、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用してソリューションをチェックアウトするか、ソリューション ファイルを取得する前に、ソース管理からプロジェクトを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="0b317-105">If a local copy of the solution does not exist on your local disk, you must open the project from source control before you can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to check out the solution or retrieve solution files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0b317-106">ソース管理から開くソリューションのローカル コピーが既に存在する場合は、ローカル コピーを上書きするかどうかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0b317-106">If you already have a local copy of the solution you are opening from source control, you are prompted to overwrite the local copy.</span></span>  
  
### <a name="to-open-a-solution-from-source-control"></a><span data-ttu-id="0b317-107">ソース管理からソリューションを開くには</span><span class="sxs-lookup"><span data-stu-id="0b317-107">To open a solution from source control</span></span>  
  
1.  <span data-ttu-id="0b317-108">[**ファイル**] メニューの [**ソース管理**] をポイントし、[**ソース管理から開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0b317-108">On the **File** menu, point to **Source Control**, and click **Open From Source Control**.</span></span>  
  
2.  <span data-ttu-id="0b317-109">ログオンを指示するメッセージが表示されたら、[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe にログオンします。</span><span class="sxs-lookup"><span data-stu-id="0b317-109">If prompted, log on to [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe.</span></span>  
  
3.  <span data-ttu-id="0b317-110">[ **SourceSafe からローカルプロジェクトを作成**] ダイアログボックスで、開くソリューションを含むフォルダーを選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0b317-110">In the **Create local project from SourceSafe** dialog box, select the folder that contains the solution you want to open, and click **OK**.</span></span>  
  
4.  <span data-ttu-id="0b317-111">ソリューションの作業フォルダーがローカルディスクドライブに既に存在する場合は、[**フォルダーに新しいプロジェクトを作成**する] ボックスが変更され、ローカルディレクトリが識別されます。</span><span class="sxs-lookup"><span data-stu-id="0b317-111">If a working folder for the solution already exists on your local disk drive, the **Create a new project in the folder** box changes to identify the local directory.</span></span> <span data-ttu-id="0b317-112">ソリューションの作業フォルダーが存在しない場合は、ソリューションを開くローカル ディレクトリを入力するか、[参照] をクリックしてローカル ディレクトリを選択できます。</span><span class="sxs-lookup"><span data-stu-id="0b317-112">If no working folder for the solution exists, you can type or browse to the local directory in which the solution should be opened.</span></span>  
  
5.  <span data-ttu-id="0b317-113">[**ソリューションを開く**] ダイアログボックスで、ソリューションファイルを選択し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0b317-113">In the **Open Solution** dialog box, select the solution file, and click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b317-114">参照</span><span class="sxs-lookup"><span data-stu-id="0b317-114">See Also</span></span>  
 [<span data-ttu-id="0b317-115">ソース管理からプロジェクトを開く</span><span class="sxs-lookup"><span data-stu-id="0b317-115">Open Projects from Source Control</span></span>](../../2014/database-engine/open-projects-from-source-control.md)  
  
  
