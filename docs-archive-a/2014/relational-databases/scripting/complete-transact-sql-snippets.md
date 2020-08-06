---
title: Transact-SQL スニペットの作成
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], completing snippets
- snippets [Transact-SQL], completing
- Transact-SQL snippets, completing
ms.assetid: a8316a58-bb57-485e-845f-84c23360314c
author: rothja
ms.author: jroth
ms.openlocfilehash: d90c77f72ba8ce80d26503645d9b04d795f5e503
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634904"
---
# <a name="complete-transact-sql-snippets"></a><span data-ttu-id="311a0-102">Transact-SQL スニペットの作成</span><span class="sxs-lookup"><span data-stu-id="311a0-102">Complete Transact-SQL Snippets</span></span>
  <span data-ttu-id="311a0-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] コード スニペットがスクリプトに挿入されると、スニペットのコンテンツを編集して [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="311a0-103">Once a [!INCLUDE[tsql](../../includes/tsql-md.md)] code snippet has been inserted into a script, you edit the contents of the snippet to build a complete [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
## <a name="completing-snippets"></a><span data-ttu-id="311a0-104">スニペットの作成</span><span class="sxs-lookup"><span data-stu-id="311a0-104">Completing Snippets</span></span>  
 <span data-ttu-id="311a0-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] スニペットをスクリプトに追加した場合、挿入されたスニペット ステートメントには 1 つ以上の置換ポイントが含まれ、強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="311a0-105">When you add a [!INCLUDE[tsql](../../includes/tsql-md.md)] snippet to your script, the inserted snippet statement has one or more replacement points, which are highlighted.</span></span> <span data-ttu-id="311a0-106">置換ポイント上にマウス ポインターを置くと、指定できる構文要素の説明を含むツールヒントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="311a0-106">If you rest your mouse pointer on a replacement point, a tooltip appears with a description of the syntax element you can specify.</span></span> <span data-ttu-id="311a0-107">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターは、ソース ファイルを閉じるまで、スニペットを周囲のスクリプトと区別します。</span><span class="sxs-lookup"><span data-stu-id="311a0-107">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor recognizes the snippet as separate from the surrounding script until you close the source file.</span></span> <span data-ttu-id="311a0-108">ソース ファイルを閉じるまで、置換ポイントはアクティブのままになります。</span><span class="sxs-lookup"><span data-stu-id="311a0-108">The replacement points remain active until you close the source file.</span></span>  
  
 <span data-ttu-id="311a0-109">スニペットによって挿入されたテンプレート コードに追加の構文要素も追加できます。</span><span class="sxs-lookup"><span data-stu-id="311a0-109">You can also add additional syntax elements to the template code inserted by a snippet.</span></span> <span data-ttu-id="311a0-110">たとえば、テーブルの作成スニペット テンプレートは、2 列の定義を生成します。3 列以上のテーブルを作成するには、列定義を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="311a0-110">For example, the Create Table snippet template generates two column definitions; you must add additional column definitions to create a table with more than two columns.</span></span>  
  
#### <a name="completing-the-snippet-statement"></a><span data-ttu-id="311a0-111">スニペット ステートメントの作成</span><span class="sxs-lookup"><span data-stu-id="311a0-111">Completing the Snippet Statement</span></span>  
  
1.  <span data-ttu-id="311a0-112">1 つの置換ポイントから次の置換ポイントに移動するには、Tab キーを使用します。</span><span class="sxs-lookup"><span data-stu-id="311a0-112">Use the TAB key to move from one replacement point to the next.</span></span> <span data-ttu-id="311a0-113">前の置換ポイントに移動するには、Shift キーを押しながら Tab キーを押します。</span><span class="sxs-lookup"><span data-stu-id="311a0-113">Use SHIFT+TAB to move to the previous replacement point.</span></span>  
  
2.  <span data-ttu-id="311a0-114">IntelliSense を呼び出すには、Ctrl キーを押しながら Space キーを押します。</span><span class="sxs-lookup"><span data-stu-id="311a0-114">Click CTRL+SPACE to invoke IntelliSense.</span></span>  
  
3.  <span data-ttu-id="311a0-115">一覧からアイテムを選択するか、置換を入力します。</span><span class="sxs-lookup"><span data-stu-id="311a0-115">Select an item from the list, or type a replacement of your choice.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="311a0-116">参照</span><span class="sxs-lookup"><span data-stu-id="311a0-116">See Also</span></span>  
 <span data-ttu-id="311a0-117">[Transact-SQL スニペットの挿入](insert-transact-sql-snippets.md) </span><span class="sxs-lookup"><span data-stu-id="311a0-117">[Insert Transact-SQL Snippets](insert-transact-sql-snippets.md) </span></span>  
 [<span data-ttu-id="311a0-118">ブロックの挿入 Transact-SQL スニペットの挿入</span><span class="sxs-lookup"><span data-stu-id="311a0-118">Insert Surround-with Transact-SQL snippets</span></span>](insert-surround-with-transact-sql-snippets.md)  
  
  
