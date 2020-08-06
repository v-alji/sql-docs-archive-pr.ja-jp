---
title: カーソルの種類 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- cursors [ODBC], types
- ODBC cursors, types
ms.assetid: 3a916cc7-f352-42cb-8b83-f78e06cef991
author: rothja
ms.author: jroth
ms.openlocfilehash: 6937dbb9ce42cd5631201e0c97be42b211742ada
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634534"
---
# <a name="cursor-types"></a><span data-ttu-id="f0ac0-102">カーソルの種類</span><span class="sxs-lookup"><span data-stu-id="f0ac0-102">Cursor Types</span></span>
  <span data-ttu-id="f0ac0-103">ODBC では、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と Native CLIENT ODBC ドライバーでサポートされる4種類のカーソルを定義して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] います。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-103">ODBC defines four cursor types supported by Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="f0ac0-104">これらのカーソルは、結果セットへの変更や、 **tempdb**のメモリや領域など、使用するリソースに対する変更を検出する機能によって異なります。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-104">These cursors vary in their ability to detect changes to the result set and in the resources they consume, such as memory and space in **tempdb**.</span></span> <span data-ttu-id="f0ac0-105">カーソルが行への変更を検出できるのは、変更が加えられた行の再フェッチを試みたときだけです。現在フェッチしている行への変更を、データ ソースからカーソルに通知する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-105">A cursor can detect changes to rows only when it tries to refetch those rows; there is no way for the data source to notify the cursor of changes to the currently fetched rows.</span></span> <span data-ttu-id="f0ac0-106">カーソルを使用して行われなかった変更を検出する機能は、トランザクション分離レベルによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-106">A cursor's ability to detect changes that were not made through the cursor is also influenced by the transaction isolation level.</span></span>  
  
 <span data-ttu-id="f0ac0-107">次に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされる 4 種類の ODBC カーソルを示します。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-107">These are the four ODBC cursor types supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="f0ac0-108">順方向専用カーソルではスクロールがサポートされず、カーソルの最初から最後まで行を順番にフェッチする機能だけがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-108">Forward-only cursors do not support scrolling; they only support fetching rows serially from the start to the end of the cursor.</span></span>  
  
-   <span data-ttu-id="f0ac0-109">静的カーソルは、カーソルを開いたときに**tempdb**に構築されます。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-109">Static cursors are built in **tempdb** when the cursor is opened.</span></span> <span data-ttu-id="f0ac0-110">静的カーソルは、常に、カーソルを開いた時点の結果セットを表示します。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-110">They always display the result set as it was when the cursor was opened.</span></span> <span data-ttu-id="f0ac0-111">データへの変更は反映されません。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-111">They never reflect changes to the data.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f0ac0-112">の静的カーソルは常に読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-112">static cursors are always read-only.</span></span> <span data-ttu-id="f0ac0-113">静的サーバーカーソルは作業テーブルとして**tempdb**に作成されるので、カーソルの結果セットのサイズは、で許容される最大行サイズを超えることはできません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-113">Because a static server cursor is built as a work table in **tempdb**, the size of the cursor result set cannot exceed the maximum row size allowed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="f0ac0-114">キーセット ドリブン カーソルでは、カーソルを開くときに、結果セット内の行のメンバーシップと順序が固定されます。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-114">Keyset-driven cursors have the membership and order of rows in the result set fixed when the cursor is opened.</span></span> <span data-ttu-id="f0ac0-115">非キー列の変更は、このカーソルを使用して表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-115">Changes to nonkey columns are visible through the cursor.</span></span>  
  
-   <span data-ttu-id="f0ac0-116">動的カーソルは静的カーソルと対照的です。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-116">Dynamic cursors are the opposite of static cursors.</span></span> <span data-ttu-id="f0ac0-117">動的カーソルでは、結果セット内の行に対するすべての変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-117">Dynamic cursors reflect all changes made to the rows in their result set.</span></span> <span data-ttu-id="f0ac0-118">結果セット内の行のデータ値、順序、およびメンバーシップは、フェッチを実行するたびに変化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f0ac0-118">The data values, order, and membership of the rows in the result set can change on each fetch.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ac0-119">参照</span><span class="sxs-lookup"><span data-stu-id="f0ac0-119">See Also</span></span>  
 [<span data-ttu-id="f0ac0-120">ODBC&#41;&#40;カーソルの使用</span><span class="sxs-lookup"><span data-stu-id="f0ac0-120">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
