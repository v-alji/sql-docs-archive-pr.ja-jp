---
title: クエリおよびビューデザイナーで各種言語データを使用する方法 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Visual Database Tools [SQL Server], international data
- queries [SQL Server], international data
- languages [SQL Server], Query and View Designer
- international considerations [SQL Server], Query and View Designer
- Criteria pane
- View Designer, international data
- Query Designer [SQL Server], international data
- localized information in Query and View Designer [SQL Server]
- global considerations [SQL Server], Query and View Designer
- SQL pane [Visual Database Tools]
- multiple language support [SQL Server], Query and View Designer
ms.assetid: 4b51c56f-f902-4e72-b919-e36127369b63
author: stevestein
ms.author: sstein
ms.openlocfilehash: 905e4c6909c792b019c11ef95662a7ec1a113bb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719292"
---
# <a name="use-the-query-and-view-designer-with-international-data-visual-database-tools"></a><span data-ttu-id="f240c-102">クエリおよびビュー デザイナーで各種言語データを使用する方法 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f240c-102">Use the Query and View Designer with International Data (Visual Database Tools)</span></span>
  <span data-ttu-id="f240c-103">[クエリおよびビュー デザイナー](visual-database-tools.md) は、あらゆる言語のデータ、および Windows オペレーティング システムのすべてのバージョンのデータに対応しています。</span><span class="sxs-lookup"><span data-stu-id="f240c-103">You can use the [Query and View Designer](visual-database-tools.md) with data in any language and in any version of the Windows operating system.</span></span> <span data-ttu-id="f240c-104">次のガイドラインでは、各種言語のアプリケーションの相違点を示し、そのデータを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f240c-104">The following guidelines outline the differences you will notice and provide information about managing data in international applications.</span></span>  
  
## <a name="localized-information-in-the-criteria-and-sql-panes"></a><span data-ttu-id="f240c-105">抽出条件ペインおよび SQL ペインのローカライズされた情報</span><span class="sxs-lookup"><span data-stu-id="f240c-105">Localized Information in the Criteria and SQL Panes</span></span>  
 <span data-ttu-id="f240c-106">抽出条件ペインを使用してクエリを作成する場合は、使用しているコンピューターの Windows 地域設定に対応する形式で情報を入力できます。</span><span class="sxs-lookup"><span data-stu-id="f240c-106">If you are using the Criteria pane to create your query, you can enter information in the format that corresponds to the Windows Regional Settings for you computer.</span></span> <span data-ttu-id="f240c-107">たとえば、データを検索する場合は、使い慣れている形式でデータを [抽出条件] 列に入力できます。ただし、次に示す場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="f240c-107">For example, if you are searching for data, you can enter the data in the Criteria columns using whatever format you are accustomed to using, with these exceptions:</span></span>  
  
-   <span data-ttu-id="f240c-108">長いデータ形式はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f240c-108">Long data formats are not supported.</span></span>  
  
-   <span data-ttu-id="f240c-109">抽出条件ペインに通貨記号を入力することはできません。</span><span class="sxs-lookup"><span data-stu-id="f240c-109">Currency symbols should not be entered in the Criteria pane.</span></span>  
  
-   <span data-ttu-id="f240c-110">通貨記号は結果ペインには表示されません。</span><span class="sxs-lookup"><span data-stu-id="f240c-110">Currency symbols will not display in the Results pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f240c-111">結果ペインでは、使用するコンピューターの Windows 地域設定に対応する通貨記号を入力できますが、その記号は削除され、結果ペインにも表示されません。</span><span class="sxs-lookup"><span data-stu-id="f240c-111">In the Results pane, you can actually enter the currency symbol that corresponds to the Windows Regional Settings for your computer, but the symbol will be removed and will not display in the Results pane.</span></span>  
  
-   <span data-ttu-id="f240c-112">[地域のオプション] での設定に関係なく、単項のマイナスは常に左側に表示されます (例 : -1)。</span><span class="sxs-lookup"><span data-stu-id="f240c-112">Unary minus always appears on the left side (for example, -1) regardless of the Regional Settings options.</span></span>  
  
 <span data-ttu-id="f240c-113">一方、SQL ペインのデータとキーワードでは、常に ANSI (U.S.) 形式を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f240c-113">In contrast, data and keywords in the SQL pane must always be in ANSI (U.S.) format.</span></span> <span data-ttu-id="f240c-114">たとえば、クエリおよびビュー デザイナーがクエリを作成する場合、SELECT や FROM などの SQL キーワードはすべて ANSI 形式で挿入されます。</span><span class="sxs-lookup"><span data-stu-id="f240c-114">For example, as the Query and View Designer builds a query, it inserts the ANSI form of all SQL keywords such as SELECT and FROM.</span></span> <span data-ttu-id="f240c-115">SQL ペインのステートメントに要素を追加する場合は、ANSI 標準規格の形式を使用してください。</span><span class="sxs-lookup"><span data-stu-id="f240c-115">If you add elements to the statement in the SQL pane, be sure to use the ANSI standard form for the elements.</span></span>  
  
 <span data-ttu-id="f240c-116">抽出条件ペインに入力した地域固有の形式のデータは、クエリおよびビュー デザイナーによって、SQL ペインでは自動的に ANSI 形式に変換されます。</span><span class="sxs-lookup"><span data-stu-id="f240c-116">When you enter data using local-specific format in the Criteria pane, the Query and View Designer automatically translates it to ANSI format in the SQL pane.</span></span> <span data-ttu-id="f240c-117">たとえば、[ロケール (国または地域)] に [ドイツ語 (ドイツ)] が設定されている場合は、抽出条件ペインでは「31.12.96」のような形式で日付を入力できます。</span><span class="sxs-lookup"><span data-stu-id="f240c-117">For example, if your Regional Settings are set to Standard German, you can enter data in the Criteria pane in a format such as "31.12.96."</span></span> <span data-ttu-id="f240c-118">しかし SQL ペインでは、このデータは `{ ts '1996-12-31 00:00:00' }.` のように ANSI 形式の日付で表示されます。SQL ペインに直接データを入力する場合は、ANSI 形式で入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f240c-118">However, the date will appear in the SQL pane in ANSI datetime format as `{ ts '1996-12-31 00:00:00' }.` If you enter data directly in the SQL pane, you must enter it in ANSI format.</span></span>  
  
## <a name="sort-order"></a><span data-ttu-id="f240c-119">並べ替え順序</span><span class="sxs-lookup"><span data-stu-id="f240c-119">Sort Order</span></span>  
 <span data-ttu-id="f240c-120">クエリにおけるデータの並べ替え順序は、データベースによって決まります。</span><span class="sxs-lookup"><span data-stu-id="f240c-120">The sort order of data in your query is determined by the database.</span></span> <span data-ttu-id="f240c-121">Windows の [地域のオプション] ダイアログ ボックスで設定したオプションは、クエリの並べ替え順序には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="f240c-121">Options that you set in the Windows Regional Settings dialog box do not affect sort order for queries.</span></span> <span data-ttu-id="f240c-122">ただし、特定のクエリで、特定の順序で行を返すように要求することはできます。</span><span class="sxs-lookup"><span data-stu-id="f240c-122">Within any particular query, however, you can request that rows be returned in a particular order.</span></span>  
  
## <a name="using-double-byte-characters"></a><span data-ttu-id="f240c-123">2 バイト文字の使用</span><span class="sxs-lookup"><span data-stu-id="f240c-123">Using Double-Byte Characters</span></span>  
 <span data-ttu-id="f240c-124">リテラルとして、またはテーブル名、ビュー名、エイリアスなどのデータベース オブジェクト名として、DBCS (2 バイト文字セット) 文字を入力できます。</span><span class="sxs-lookup"><span data-stu-id="f240c-124">You can enter DBCS characters for literals and for database object names such as table and view names or aliases.</span></span> <span data-ttu-id="f240c-125">DBCS 文字は、パラメーター名およびパラメーター マーカー文字にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f240c-125">You can also use DBCS characters for parameter names and parameter marker characters.</span></span> <span data-ttu-id="f240c-126">ただし、関数名や SQL キーワードなどの SQL 言語要素に DBCS 文字を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f240c-126">However, you cannot use DBCS characters in SQL language elements such as function names or SQL keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f240c-127">参照</span><span class="sxs-lookup"><span data-stu-id="f240c-127">See Also</span></span>  
 [<span data-ttu-id="f240c-128">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f240c-128">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
