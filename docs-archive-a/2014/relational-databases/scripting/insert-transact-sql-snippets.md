---
title: Transact-SQL スニペットの挿入
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], snippets
- Transact-SQL snippets, code
- snippets [Transact-SQL], how to insert
ms.assetid: d66c96f4-2e84-4d79-9bfd-3635fdd98425
author: rothja
ms.author: jroth
ms.openlocfilehash: 26a7a224e700c726ee3d4437321843d45ddb6e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644979"
---
# <a name="insert-transact-sql-snippets"></a><span data-ttu-id="6a4c3-102">Transact-SQL スニペットの挿入</span><span class="sxs-lookup"><span data-stu-id="6a4c3-102">Insert Transact-SQL Snippets</span></span>
  <span data-ttu-id="6a4c3-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] コード スニペットは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリ エディターで [!INCLUDE[ssDE](../../includes/ssde-md.md)] ステートメントを新規作成するときの開始位置として使用できるテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="6a4c3-103">A [!INCLUDE[tsql](../../includes/tsql-md.md)] code snippet is a template you can use as a starting point when writing new [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
## <a name="inserting-snippets"></a><span data-ttu-id="6a4c3-104">スニペットの挿入</span><span class="sxs-lookup"><span data-stu-id="6a4c3-104">Inserting Snippets</span></span>  
 <span data-ttu-id="6a4c3-105">**[スニペットの挿入]** メニューを使用して、スニペットのカテゴリ別一覧からスニペットを選択できます。</span><span class="sxs-lookup"><span data-stu-id="6a4c3-105">You can use the **Insert Snippet** menu to open a categorized list of snippets to choose from.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="6a4c3-106">スニペットには、置換ポイント (そのポイントに関連する構文を示すテキスト) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6a4c3-106">snippets contain replacement points: text that suggests the syntax relevant to that point.</span></span> <span data-ttu-id="6a4c3-107">たとえば、CREATE TABLE スニペットには、テーブル名、列名、列のデータ型などの要素の置換ポイントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6a4c3-107">For example, the CREATE TABLE snippet has replacement points for elements such as the table name, column names, and column data types.</span></span> <span data-ttu-id="6a4c3-108">このスニペットを挿入した後は、置換テキストを変更して、有効な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a4c3-108">After inserting the snippet, you must change the replacement text to form a valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="6a4c3-109">詳細については、「 [Transact-SQL スニペットの作成](complete-transact-sql-snippets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a4c3-109">For more information, see [Complete Transact-SQL Snippets](complete-transact-sql-snippets.md).</span></span>  
  
#### <a name="inserting-a-snippet-by-using-the-insert-snippet-menu"></a><span data-ttu-id="6a4c3-110">[スニペットの挿入] メニューを使用したスニペットの挿入</span><span class="sxs-lookup"><span data-stu-id="6a4c3-110">Inserting a Snippet by Using the Insert Snippet Menu</span></span>  
  
1.  <span data-ttu-id="6a4c3-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター ウィンドウで、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スニペットを挿入する位置にカーソルを置きます。</span><span class="sxs-lookup"><span data-stu-id="6a4c3-111">In the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window, put the cursor where you want to insert the [!INCLUDE[tsql](../../includes/tsql-md.md)] snippet.</span></span>  
  
2.  <span data-ttu-id="6a4c3-112">次の 3 つのうちいずれかの方法でスニペット ピッカーのヒントを起動します。</span><span class="sxs-lookup"><span data-stu-id="6a4c3-112">Launch the snippet picker tooltip in one of three ways:</span></span>  
  
    -   <span data-ttu-id="6a4c3-113">Ctrl キーを押しながら K キーを押し、Ctrl キーを押しながら X キーを押す。</span><span class="sxs-lookup"><span data-stu-id="6a4c3-113">Press CTRL+K, CTRL+X.</span></span>  
  
    -   <span data-ttu-id="6a4c3-114">**[編集]** メニューの **[IntelliSense]** をポイントし、 **[スニペットの挿入]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="6a4c3-114">On the **Edit** menu, point to **IntelliSense**, then click **Insert Snippet**.</span></span>  
  
    -   <span data-ttu-id="6a4c3-115">右クリックし、ショートカット メニューの **[スニペットの挿入]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="6a4c3-115">Right-click the mouse and then select the **Insert Snippet** command from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="6a4c3-116">スニペットをダブルクリックするか、スニペット ピッカーからスニペットを選択して、Tab キーまたは Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6a4c3-116">Double-click the snippet, or select the snippet from the snippet picker and then press TAB or ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a4c3-117">参照</span><span class="sxs-lookup"><span data-stu-id="6a4c3-117">See Also</span></span>  
 [<span data-ttu-id="6a4c3-118">ブロックの挿入 Transact-SQL スニペットの挿入</span><span class="sxs-lookup"><span data-stu-id="6a4c3-118">Insert Surround-with Transact-SQL snippets</span></span>](insert-surround-with-transact-sql-snippets.md)  
  
  
