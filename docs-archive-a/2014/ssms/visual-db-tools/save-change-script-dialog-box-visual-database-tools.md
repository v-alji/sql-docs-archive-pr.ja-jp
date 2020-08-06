---
title: '[変更スクリプトの保存] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.generatechangescript
- vdtsql.chm:65544
ms.assetid: fc9d1639-5efa-44fe-a04f-4d4d0def2833
author: stevestein
ms.author: sstein
ms.openlocfilehash: 19a2bb2ce9a219c195421e2efa203fc115e1ae1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711405"
---
# <a name="save-change-script-dialog-box-visual-database-tools"></a><span data-ttu-id="e0554-102">[変更スクリプトの保存] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e0554-102">Save Change Script Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="e0554-103">このダイアログ ボックスには、最後にテーブルを保存してから、変更を行った [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0554-103">This dialog box shows the [!INCLUDE[tsql](../../includes/tsql-md.md)] script for the changes you have made since you last saved the table.</span></span> <span data-ttu-id="e0554-104">選択した場所に、テキスト ファイル形式でスクリプトを保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="e0554-104">It also allows you to save the script to a text file at a location you choose.</span></span>  
  
 <span data-ttu-id="e0554-105">テーブル デザイナーのテーブルへの変更を保存しなかった場合に、このダイアログ ボックスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e0554-105">You can access this dialog box after you have made unsaved changes to a table in Table Designer.</span></span> <span data-ttu-id="e0554-106">**[テーブル デザイナー]** メニューの **[変更スクリプトの生成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0554-106">On the **Table Designer** menu, click **Generate Change Script**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e0554-107">Visual Database Tools によって提供される変更スクリプトにはエラー処理は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="e0554-107">Change scripts provided by Visual Database Tools contain no error handling.</span></span> <span data-ttu-id="e0554-108">ツールが開いた後でデータベース オブジェクトが変更されていないことを前提としているため、変換関連の問題が発生することを想定していません。</span><span class="sxs-lookup"><span data-stu-id="e0554-108">They assume that database objects have not changed since the tool was opened, and that change-related problems will therefore not occur.</span></span> <span data-ttu-id="e0554-109">変更スクリプトを実行する前に、適切なエラー処理ステートメントを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0554-109">Before running a change script, you should include the appropriate error-handling statements.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e0554-110">オプション</span><span class="sxs-lookup"><span data-stu-id="e0554-110">Options</span></span>  
 <span data-ttu-id="e0554-111">**[保存時に変更スクリプトを自動作成する]**</span><span class="sxs-lookup"><span data-stu-id="e0554-111">**Automatically generate change script on every save**</span></span>  
 <span data-ttu-id="e0554-112">オンにすると、テーブルへの変更を保存するときに毎回 **[変更スクリプトの保存]** ダイアログ ボックスが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="e0554-112">If checked, the **Save Change Script** dialog box will appear any time you save changes to a table.</span></span>  
  
 <span data-ttu-id="e0554-113">**はい**</span><span class="sxs-lookup"><span data-stu-id="e0554-113">**Yes**</span></span>  
 <span data-ttu-id="e0554-114">テキスト ファイルの場所を選択できる **[上書き保存]** ダイアログ ボックスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e0554-114">Bring up the **Save** dialog box where you can choose the location for the text file.</span></span>  
  
 <span data-ttu-id="e0554-115">**いいえ**</span><span class="sxs-lookup"><span data-stu-id="e0554-115">**No**</span></span>  
 <span data-ttu-id="e0554-116">変更スクリプトの作成を取り消します。</span><span class="sxs-lookup"><span data-stu-id="e0554-116">Cancel the creation of the change script.</span></span>  
  
  
