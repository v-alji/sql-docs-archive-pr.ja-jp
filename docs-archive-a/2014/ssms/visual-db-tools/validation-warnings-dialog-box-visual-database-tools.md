---
title: '[評価に関する警告] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65556
- vdt.dlgbox.validationwarnings
ms.assetid: fc76e234-ec9c-4a19-a65b-cb558ec8268e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4f94c3ae91e077af853db949847bc8448f6a4753
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641926"
---
# <a name="validation-warnings-dialog-box-visual-database-tools"></a><span data-ttu-id="8e6c7-102">[評価に関する警告] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8e6c7-102">Validation Warnings Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="8e6c7-103">このダイアログ ボックスは、データベースに悪影響を及ぼす可能性のある変更を保存しようとした場合、またはデータベースのコミット動作が失敗する可能性がある場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-103">This dialog box appears if you attempt to save modifications with potentially damaging side effects, or if the database commit operation is likely to fail.</span></span> <span data-ttu-id="8e6c7-104">このダイアログ ボックスには、可能性のある具体的な悪影響またはコミット動作が失敗する理由が示されます。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-104">This dialog box indicates what those side effects might be or why the commit operation might fail.</span></span> <span data-ttu-id="8e6c7-105">このまま変更を保存するか取り消すかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-105">It gives you the chance to continue with the modification or cancel the operation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e6c7-106">このダイアログ ボックスは、変更をデータベースに適用しようとしたとき、または変更スクリプトを保存したときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-106">This dialog box appears when you attempt to transmit your modifications to the database or when you save a change script.</span></span>  
  
 <span data-ttu-id="8e6c7-107">このダイアログ ボックスは、次のような理由によって表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-107">The dialog box can appear for any of these reasons:</span></span>  
  
-   <span data-ttu-id="8e6c7-108">すべての変更をコミットするためのデータベース アクセス許可を持っていない。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-108">You might not have database permissions to commit all the modifications.</span></span>  
  
-   <span data-ttu-id="8e6c7-109">変更によって、派生された列、既定の制約、または CHECK 制約が不適切に形成される。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-109">Your modifications would result in improperly formed derived columns, default constraints, or check constraints.</span></span>  
  
-   <span data-ttu-id="8e6c7-110">列のデータ型を変更することでデータの損失が発生する。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-110">A modification to a column's data type might cause data loss.</span></span>  
  
-   <span data-ttu-id="8e6c7-111">変更によって 900 バイトを超えるインデックスが生成される。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-111">A modification would result in an index greater than 900 bytes.</span></span>  
  
-   <span data-ttu-id="8e6c7-112">変更によって、スキーマ連結ビューやユーザー定義関数で使用されるテーブルまたは列が変更される。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-112">A modification would change a table or column contributing to a schema-bound view or user-defined function.</span></span>  
  
-   <span data-ttu-id="8e6c7-113">変更によって、1 つ以上の暗号化されたトリガーを含むテーブルが再作成され、トリガーが無効になる。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-113">A modification would result in the re-creation of a table that has one or more encrypted triggers; the triggers will be dropped.</span></span>  
  
-   <span data-ttu-id="8e6c7-114">変更によって、1 つのテーブル内の列に対して ANSI_NULLS と ANSI_PADDING のいずれかまたは両方に意味のある設定がされる。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-114">Your modifications will yield noteworthy settings of ANSI_NULLS or ANSI_PADDING or both for the columns within one table.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8e6c7-115">オプション</span><span class="sxs-lookup"><span data-stu-id="8e6c7-115">Options</span></span>  
 <span data-ttu-id="8e6c7-116">**はい**</span><span class="sxs-lookup"><span data-stu-id="8e6c7-116">**Yes**</span></span>  
 <span data-ttu-id="8e6c7-117">操作を続行し、変更スクリプトを生成するか、変更をデータベースに転送します。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-117">Proceed with the operation and generate the change script or transmit the modifications to the database.</span></span> <span data-ttu-id="8e6c7-118">データベースを変更する権限を持っていない場合、変更によってインデックスが 900 バイトを超える場合、または変更の結果として計算される列、既定の制約、CHECK 制約が正しく作成されない場合に、コミット操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-118">The commit operation can still fail if you do not have privileges to modify the database, if your modifications will result in an index greater than 900 bytes, or if your modifications will result in an improperly formed computed column, default constraint, or check constraint.</span></span>  
  
 <span data-ttu-id="8e6c7-119">**いいえ**</span><span class="sxs-lookup"><span data-stu-id="8e6c7-119">**No**</span></span>  
 <span data-ttu-id="8e6c7-120">保存操作を取り消します。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-120">Cancel the save action.</span></span>  
  
 <span data-ttu-id="8e6c7-121">**[テキスト ファイルを保存]**</span><span class="sxs-lookup"><span data-stu-id="8e6c7-121">**Save Text File**</span></span>  
 <span data-ttu-id="8e6c7-122">**[名前を付けて保存]** ダイアログ ボックスを表示し、警告リストを含むテキスト ファイルの保存場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8e6c7-122">Display the **Save As** dialog box, where you can specify a location for a text file containing a list of the warnings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e6c7-123">参照</span><span class="sxs-lookup"><span data-stu-id="8e6c7-123">See Also</span></span>  
 <span data-ttu-id="8e6c7-124">[Visual Database Tools &#40;テーブルのデザイン&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="8e6c7-124">[Design Tables &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="8e6c7-125">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8e6c7-125">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
