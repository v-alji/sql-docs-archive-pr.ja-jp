---
title: エディターの構成
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: e7c7a8ef-f561-4258-a7b6-c445dba69f87
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e94cdbcd310814081e146e3fd0dbe75260d1240
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716222"
---
# <a name="configure-editors-sql-server-management-studio"></a><span data-ttu-id="8ee39-102">エディターの構成 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="8ee39-102">Configure Editors (SQL Server Management Studio)</span></span>
  <span data-ttu-id="8ee39-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] エディターのオプションを構成することにより、各エディターの操作をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="8ee39-103">You can customize the operation of the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] editors by configuring the options for each editor.</span></span>  
  
## <a name="settng-editor-options"></a><span data-ttu-id="8ee39-104">エディター オプションの設定</span><span class="sxs-lookup"><span data-stu-id="8ee39-104">Settng Editor Options</span></span>  
 <span data-ttu-id="8ee39-105">ほとんどのエディター オプションは、 **[ツール]** メニューで **[オプション]** を選択し、 **[オプション]** ダイアログを表示して設定します。</span><span class="sxs-lookup"><span data-stu-id="8ee39-105">Most of the editor options are set by using the **Tools** menu and selecting **Options...** to display an **Options** dialog.</span></span> <span data-ttu-id="8ee39-106">**[オプション]** ダイアログの左ペインの **[テキスト エディター]** ノードを開いて、コードとテキストの編集オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="8ee39-106">In the **Options** dialog, open the **Text Editor** node in the left pane to set code and text editing options.</span></span> <span data-ttu-id="8ee39-107">[テキスト エディター] の下のノードは特定のエディターに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8ee39-107">The nodes under Text Editor apply to specific editors:</span></span>  
  
1.  <span data-ttu-id="8ee39-108">**すべての言語**: このノードを使用して設定されたオプションは、すべての [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] エディターに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8ee39-108">**All Languages** - options set using this node apply to all of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] editors.</span></span> <span data-ttu-id="8ee39-109">これらの設定は、他のノードを使用して特定のエディターの別のオプションを設定することによりオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="8ee39-109">You can override these settings by using the other nodes to set different options for a specific editor.</span></span>  
  
2.  <span data-ttu-id="8ee39-110">**プレーンテキスト**: このノードを使用して設定されたオプションは、MDX エディター、DMX エディター、およびテキスト エディターに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8ee39-110">**Plain Text** - options set using this node apply to the MDX, DMX, and text editors.</span></span>  
  
3.  <span data-ttu-id="8ee39-111">**Transact-SQL**: このノードを使用して設定されたオプションは、データベース エンジン クエリ エディターに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8ee39-111">**Transact-SQL** - options set using this node apply to the Database Engine Query Editor.</span></span>  
  
4.  <span data-ttu-id="8ee39-112">**XML**: このノードを使用して設定されたオプションは、XML for Analysis エディターに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8ee39-112">**XML** - options set using this node apply to the XML for Analysis editor.</span></span>  
  
 <span data-ttu-id="8ee39-113">**[クエリ実行]** または **[クエリ結果]** ノードを開いて、クエリの実行やクエリ結果の表示方法をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="8ee39-113">Open the **Query Execution** or **Query Results** nodes to customize the execution of queries and how the results are displayed.</span></span>  
  
## <a name="editor-configuration-tasks"></a><span data-ttu-id="8ee39-114">エディターの構成タスク</span><span class="sxs-lookup"><span data-stu-id="8ee39-114">Editor Configuration Tasks</span></span>  
  
|<span data-ttu-id="8ee39-115">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="8ee39-115">Task Description</span></span>|<span data-ttu-id="8ee39-116">トピック</span><span class="sxs-lookup"><span data-stu-id="8ee39-116">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="8ee39-117">エクスプローラーで、指定された拡張子を持つファイルをダブルクリックしたときに開かれるエディターを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ee39-117">Describes how to specify that an editor be opened by double-clicking on a file with a specified extension in Windows Explorer.</span></span>|[<span data-ttu-id="8ee39-118">ファイル拡張子をコード エディターに関連付ける方法</span><span class="sxs-lookup"><span data-stu-id="8ee39-118">Associate File Extensions to a Code Editor</span></span>](associate-file-extensions-to-a-code-editor.md)|  
|<span data-ttu-id="8ee39-119">コードおよびテキストを読みやすくするためにフォントをカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ee39-119">Describes how to customize fonts to make code and text more readable.</span></span>|[<span data-ttu-id="8ee39-120">フォントの色、サイズ、スタイルを変更する方法</span><span class="sxs-lookup"><span data-stu-id="8ee39-120">Change Font Color, Size, and Style</span></span>](change-font-color-size-and-style.md)|  
|<span data-ttu-id="8ee39-121">プロパティの表示方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ee39-121">Describes how to view properties.</span></span>|<span data-ttu-id="8ee39-122">[Management Studio の [プロパティ] ウィンドウの使用](use-the-properties-window-in-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="8ee39-122">[Use the Properties Window in Management Studio](use-the-properties-window-in-management-studio.md)</span></span>|  
|<span data-ttu-id="8ee39-123">エディター オプション ダイアログの F1 ヘルプ ページの場所です。</span><span class="sxs-lookup"><span data-stu-id="8ee39-123">Location of the F1 help pages for the editor options dialogs.</span></span>|<span data-ttu-id="8ee39-124">[[クエリ オプション] ページの F1 ヘルプ](../../database-engine/query-options-pages-f1-help.md)</span><span class="sxs-lookup"><span data-stu-id="8ee39-124">[Query Options Pages F1 Help](../../database-engine/query-options-pages-f1-help.md)</span></span>|  
  
  
