---
title: データベースダイアグラム間でのテーブルのコピー (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- duplicating tables
ms.assetid: 155a4f09-9321-4887-a7d4-aa2ce6b51277
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7e90c8f324e80f7c59674def06a77e93a5bf0cb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711450"
---
# <a name="copy-tables-from-one-database-diagrams-to-another-visual-database-tools"></a><span data-ttu-id="112c4-102">データベース ダイアグラム間でのテーブルのコピー (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="112c4-102">Copy Tables from One Database Diagrams to Another (Visual Database Tools)</span></span>
  <span data-ttu-id="112c4-103">データベース ダイアグラムから同じデータベースの他のデータベース ダイアグラムにテーブルをコピーできます。</span><span class="sxs-lookup"><span data-stu-id="112c4-103">You can copy a table from one database diagram to another in the same database.</span></span>  
  
 <span data-ttu-id="112c4-104">データベース ダイアグラム間でテーブルをコピーすると、コピー先のダイアグラムのテーブルに参照が追加されます。</span><span class="sxs-lookup"><span data-stu-id="112c4-104">Copying a table from one database diagram to another diagram adds a reference to the table in the second diagram.</span></span> <span data-ttu-id="112c4-105">テーブルがデータベースに複製されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="112c4-105">The table is not duplicated in your database.</span></span> <span data-ttu-id="112c4-106">たとえば、データベース ダイアグラム間で `authors` テーブルをコピーすると、各ダイアグラムはデータベースの同じ `authors` テーブルを参照します。</span><span class="sxs-lookup"><span data-stu-id="112c4-106">For example, if you copy the `authors` table from one database diagram to another, each diagram references the same `authors` table in the database.</span></span>  
  
### <a name="to-copy-a-table-from-another-database-diagram"></a><span data-ttu-id="112c4-107">他のデータベース ダイアグラムからテーブルをコピーするには</span><span class="sxs-lookup"><span data-stu-id="112c4-107">To copy a table from another database diagram</span></span>  
  
1.  <span data-ttu-id="112c4-108">テーブルをコピーするデータベースに接続していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="112c4-108">Make sure you are connected to the database whose table you want to copy.</span></span>  
  
2.  <span data-ttu-id="112c4-109">コピー元およびコピー先のデータベース ダイアグラムを開き、コピー元のダイアグラムで、コピー先のダイアグラムにコピーするテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="112c4-109">Open the source and target database diagrams and within the source diagram, select the table that you want to copy to the target diagram.</span></span>  
  
3.  <span data-ttu-id="112c4-110">ツール バーの **[コピー]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="112c4-110">Click the **Copy** button on the toolbar.</span></span> <span data-ttu-id="112c4-111">選択したテーブルの定義がクリップボードにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="112c4-111">This action places the selected table definition on the Clipboard.</span></span>  
  
4.  <span data-ttu-id="112c4-112">コピー先のダイアグラムに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="112c4-112">Switch to the target diagram.</span></span> <span data-ttu-id="112c4-113">このダイアグラムは、コピー元のダイアグラムと同じデータベースにある必要があります。</span><span class="sxs-lookup"><span data-stu-id="112c4-113">This diagram must be in the same database as the source diagram.</span></span>  
  
5.  <span data-ttu-id="112c4-114">ツール バーの **[貼り付け]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="112c4-114">Click the **Paste** button on the toolbar.</span></span> <span data-ttu-id="112c4-115">クリップボードの内容が新しい場所に表示され、他の場所をクリックするまで強調表示された状態が続きます。</span><span class="sxs-lookup"><span data-stu-id="112c4-115">The Clipboard contents appear at the new location and remain highlighted until you click elsewhere.</span></span> <span data-ttu-id="112c4-116">コピー先のダイアグラムで、選択したテーブルとダイアグラムの他のテーブルとの間にリレーションシップが存在する場合は、自動的にリレーションシップの線が引かれます。</span><span class="sxs-lookup"><span data-stu-id="112c4-116">If relationships exist between the selected tables and other tables in the target diagram, relationship lines are automatically drawn.</span></span>  
  
 <span data-ttu-id="112c4-117">どちらかのダイアグラムでテーブルを編集すると、両方のダイアグラムに変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="112c4-117">When you edit the table in either diagram, your changes are reflected in both diagrams.</span></span> <span data-ttu-id="112c4-118">同様に、どちらかのダイアグラムのテーブルを保存すると、どちらのダイアグラムでもテーブルは "変更済み" と見なされなくなります。</span><span class="sxs-lookup"><span data-stu-id="112c4-118">Similarly, once you save the table in either diagram, the table is no longer considered "modified" in either diagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="112c4-119">参照</span><span class="sxs-lookup"><span data-stu-id="112c4-119">See Also</span></span>  
 <span data-ttu-id="112c4-120">[データベースダイアグラムの使用 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="112c4-120">[Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="112c4-121">ダイアグラムへのテーブルの追加 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="112c4-121">Add Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](add-tables-to-diagrams-visual-database-tools.md)  
  
  
