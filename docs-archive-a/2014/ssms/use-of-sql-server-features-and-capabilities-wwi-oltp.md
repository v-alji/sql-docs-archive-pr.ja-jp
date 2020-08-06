---
title: 外部ツールの引数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- arguments [SQL Server Management Studio]
- external tools [SQL Server Management Studio]
ms.assetid: 3991c13a-f23f-450b-a2ba-19391c399735
author: stevestein
ms.author: sstein
ms.openlocfilehash: 71a7fb99eee3286d21a405e9564d046847406a1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644770"
---
# <a name="arguments-for-external-tools"></a><span data-ttu-id="d14aa-102">外部ツールの引数</span><span class="sxs-lookup"><span data-stu-id="d14aa-102">Arguments for External Tools</span></span>
  <span data-ttu-id="d14aa-103">引数とは、 **[ツール]** メニューから外部ツールを起動したときに、Studio 環境によって値が提供される変数です。</span><span class="sxs-lookup"><span data-stu-id="d14aa-103">Arguments are variables that the Studio environment supplies values for when an external tool is launched from the **Tools** menu.</span></span> <span data-ttu-id="d14aa-104">**[外部ツール]** ダイアログ ボックスを使用して、メモ帳などの外部ツールを **[ツール]** メニューに追加できます。</span><span class="sxs-lookup"><span data-stu-id="d14aa-104">External tools such as Notepad can be added to the **Tools** menu using the **External Tools** dialog box.</span></span>  
  
 <span data-ttu-id="d14aa-105">外部ツールの引数は、次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d14aa-105">The following table lists arguments for external tools.</span></span>  
  
|<span data-ttu-id="d14aa-106">Name</span><span class="sxs-lookup"><span data-stu-id="d14aa-106">Name</span></span>|<span data-ttu-id="d14aa-107">引数</span><span class="sxs-lookup"><span data-stu-id="d14aa-107">Argument</span></span>|<span data-ttu-id="d14aa-108">説明</span><span class="sxs-lookup"><span data-stu-id="d14aa-108">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="d14aa-109">**項目のパス**</span><span class="sxs-lookup"><span data-stu-id="d14aa-109">**Item Path**</span></span>|<span data-ttu-id="d14aa-110">$(ItemPath)</span><span class="sxs-lookup"><span data-stu-id="d14aa-110">$(ItemPath)</span></span>|<span data-ttu-id="d14aa-111">現在のソースの完全なファイル名 (ドライブ + パス + ファイル名として定義されます)。ソース以外のウィンドウがアクティブな場合は空白です。</span><span class="sxs-lookup"><span data-stu-id="d14aa-111">The complete file name of the current source (defined as drive + path + file name); blank if a non-source window is active.</span></span>|  
|<span data-ttu-id="d14aa-112">**項目のディレクトリ**</span><span class="sxs-lookup"><span data-stu-id="d14aa-112">**Item Directory**</span></span>|<span data-ttu-id="d14aa-113">$(ItemDir)</span><span class="sxs-lookup"><span data-stu-id="d14aa-113">$(ItemDir)</span></span>|<span data-ttu-id="d14aa-114">現在のソースのディレクトリ (ドライブ + パスとして定義されます)。ソース以外のウィンドウがアクティブな場合は空白です。</span><span class="sxs-lookup"><span data-stu-id="d14aa-114">The directory of the current source (defined as drive + path); blank if a non-source window is active.</span></span>|  
|<span data-ttu-id="d14aa-115">**項目のファイル名**</span><span class="sxs-lookup"><span data-stu-id="d14aa-115">**Item File Name**</span></span>|<span data-ttu-id="d14aa-116">$(ItemFilename)</span><span class="sxs-lookup"><span data-stu-id="d14aa-116">$(ItemFilename)</span></span>|<span data-ttu-id="d14aa-117">現在のソースのファイル名 (ファイル名として定義されます)。ソース以外のウィンドウがアクティブな場合は空白です。</span><span class="sxs-lookup"><span data-stu-id="d14aa-117">The file name of the current source (defined as file name); blank if a non-source window is active.</span></span>|  
|<span data-ttu-id="d14aa-118">**項目の拡張子**</span><span class="sxs-lookup"><span data-stu-id="d14aa-118">**Item extension**</span></span>|<span data-ttu-id="d14aa-119">$(ItemExt)</span><span class="sxs-lookup"><span data-stu-id="d14aa-119">$(ItemExt)</span></span>|<span data-ttu-id="d14aa-120">現在のソースのファイル名の拡張子。</span><span class="sxs-lookup"><span data-stu-id="d14aa-120">The file name extension of the current source.</span></span>|  
|<span data-ttu-id="d14aa-121">**現在の行** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d14aa-121">**Current Line** <sup>1</sup></span></span>|<span data-ttu-id="d14aa-122">$(CurLine)</span><span class="sxs-lookup"><span data-stu-id="d14aa-122">$(CurLine)</span></span>|<span data-ttu-id="d14aa-123">エディター内でカーソルが置かれている現在の行位置。</span><span class="sxs-lookup"><span data-stu-id="d14aa-123">The current line position of the cursor in the editor.</span></span>|  
|<span data-ttu-id="d14aa-124">**現在の列**1</span><span class="sxs-lookup"><span data-stu-id="d14aa-124">**Current Column**1</span></span>|<span data-ttu-id="d14aa-125">$(CurCol)</span><span class="sxs-lookup"><span data-stu-id="d14aa-125">$(CurCol)</span></span>|<span data-ttu-id="d14aa-126">エディター内でカーソルが置かれている現在の列位置。</span><span class="sxs-lookup"><span data-stu-id="d14aa-126">The current column position of the cursor in the editor.</span></span>|  
|<span data-ttu-id="d14aa-127">**現在のテキスト**1</span><span class="sxs-lookup"><span data-stu-id="d14aa-127">**Current Text**1</span></span>|<span data-ttu-id="d14aa-128">$(CurText)</span><span class="sxs-lookup"><span data-stu-id="d14aa-128">$(CurText)</span></span>|<span data-ttu-id="d14aa-129">現在のテキスト (現在のカーソル位置にある単語、または選択中の単一行です)。</span><span class="sxs-lookup"><span data-stu-id="d14aa-129">The current text (the word under the current cursor position, or a single-line selection, if there is one).</span></span>|  
|<span data-ttu-id="d14aa-130">**ターゲット パス**</span><span class="sxs-lookup"><span data-stu-id="d14aa-130">**Target Path**</span></span>|<span data-ttu-id="d14aa-131">$(TargetPath)</span><span class="sxs-lookup"><span data-stu-id="d14aa-131">$(TargetPath)</span></span>|<span data-ttu-id="d14aa-132">ターゲットの完全なファイル名 (ドライブ + パス + ファイル名として定義されます)。</span><span class="sxs-lookup"><span data-stu-id="d14aa-132">The complete file name of the target (defined as drive + path + file name).</span></span>|  
|<span data-ttu-id="d14aa-133">**ターゲット ディレクトリ**</span><span class="sxs-lookup"><span data-stu-id="d14aa-133">**Target Directory**</span></span>|<span data-ttu-id="d14aa-134">$(TargetDir)</span><span class="sxs-lookup"><span data-stu-id="d14aa-134">$(TargetDir)</span></span>|<span data-ttu-id="d14aa-135">ターゲットのディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="d14aa-135">The directory of the target.</span></span>|  
|<span data-ttu-id="d14aa-136">**ターゲット名**</span><span class="sxs-lookup"><span data-stu-id="d14aa-136">**Target Name**</span></span>|<span data-ttu-id="d14aa-137">$(TargetName)</span><span class="sxs-lookup"><span data-stu-id="d14aa-137">$(TargetName)</span></span>|<span data-ttu-id="d14aa-138">ターゲットのファイル名。</span><span class="sxs-lookup"><span data-stu-id="d14aa-138">The file name of the target.</span></span>|  
|<span data-ttu-id="d14aa-139">**ターゲットの拡張子**</span><span class="sxs-lookup"><span data-stu-id="d14aa-139">**Target Extension**</span></span>|<span data-ttu-id="d14aa-140">$(TargetExt)</span><span class="sxs-lookup"><span data-stu-id="d14aa-140">$(TargetExt)</span></span>|<span data-ttu-id="d14aa-141">ターゲットのファイル名の拡張子。</span><span class="sxs-lookup"><span data-stu-id="d14aa-141">The file name extension of the target.</span></span>|  
|<span data-ttu-id="d14aa-142">**プロジェクト ディレクトリ**</span><span class="sxs-lookup"><span data-stu-id="d14aa-142">**Project Directory**</span></span>|<span data-ttu-id="d14aa-143">$(ProjDir)</span><span class="sxs-lookup"><span data-stu-id="d14aa-143">$(ProjDir)</span></span>|<span data-ttu-id="d14aa-144">現在のプロジェクトのディレクトリ (ドライブ + パスとして定義されます)。</span><span class="sxs-lookup"><span data-stu-id="d14aa-144">The directory of the current project (defined as drive + path).</span></span>|  
|<span data-ttu-id="d14aa-145">**プロジェクト ファイル名**</span><span class="sxs-lookup"><span data-stu-id="d14aa-145">**Project File Name**</span></span>|<span data-ttu-id="d14aa-146">$(ProjFileName)</span><span class="sxs-lookup"><span data-stu-id="d14aa-146">$(ProjFileName)</span></span>|<span data-ttu-id="d14aa-147">現在のプロジェクトのファイル名 (ドライブ + パス + ファイル名として定義されます)。</span><span class="sxs-lookup"><span data-stu-id="d14aa-147">The file name of the current project (defined as drive + path + file name).</span></span>|  
|<span data-ttu-id="d14aa-148">**ソリューション ディレクトリ**</span><span class="sxs-lookup"><span data-stu-id="d14aa-148">**Solution Directory**</span></span>|<span data-ttu-id="d14aa-149">$(SolutionDir)</span><span class="sxs-lookup"><span data-stu-id="d14aa-149">$(SolutionDir)</span></span>|<span data-ttu-id="d14aa-150">現在のソリューションのディレクトリ (ドライブ + パスとして定義されます)。</span><span class="sxs-lookup"><span data-stu-id="d14aa-150">The directory of the current solution (defined as drive + path).</span></span>|  
|<span data-ttu-id="d14aa-151">**ソリューション ファイル名**</span><span class="sxs-lookup"><span data-stu-id="d14aa-151">**Solution File Name**</span></span>|<span data-ttu-id="d14aa-152">$(SolutionFileName)</span><span class="sxs-lookup"><span data-stu-id="d14aa-152">$(SolutionFileName)</span></span>|<span data-ttu-id="d14aa-153">現在のソリューションのファイル名 (ドライブ + パス + ファイル名として定義されます)。</span><span class="sxs-lookup"><span data-stu-id="d14aa-153">The file name of the current solution (defined as drive + path + file name).</span></span>|  
  
 <span data-ttu-id="d14aa-154"><sup>1</sup>現在の行、現在の列、または現在のテキストは、ステータスバーに表示されるテキストエディター内のカーソルの位置に基づいています。</span><span class="sxs-lookup"><span data-stu-id="d14aa-154"><sup>1</sup> The current line, current column, or current text is based on the position of the cursor in the text editor as shown in the status bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d14aa-155">参照</span><span class="sxs-lookup"><span data-stu-id="d14aa-155">See Also</span></span>  
 <span data-ttu-id="d14aa-156">[[外部ツール] ダイアログボックス](external-tools-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="d14aa-156">[External Tools Dialog Box](external-tools-dialog-box.md) </span></span>  
 [<span data-ttu-id="d14aa-157">一般的なユーザー インターフェイス要素</span><span class="sxs-lookup"><span data-stu-id="d14aa-157">General User Interface Elements</span></span>](general-user-interface-elements.md)  
  
  
