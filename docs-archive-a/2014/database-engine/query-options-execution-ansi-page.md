---
title: '[クエリオプション] の [実行] ([ANSI] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.ansi.f1
ms.assetid: c90d7cdf-3309-46f4-b900-220521bb9552
author: rothja
ms.author: jroth
ms.openlocfilehash: 013a7a318ed7f8db9156700f789ae64cf3e4e017
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720343"
---
# <a name="query-options-execution-ansi-page"></a><span data-ttu-id="dddf8-102">[クエリ オプション] の [実行] ([ANSI] ページ)</span><span class="sxs-lookup"><span data-stu-id="dddf8-102">Query Options Execution (ANSI Page)</span></span>
  <span data-ttu-id="dddf8-103">このページを使用すると、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ISO (ANSI) 規格で指定されているすべてまたは一部の設定を使用してクエリを実行するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="dddf8-103">Use this page to specify that [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will run the queries using all or a portion of the settings specified in the ISO (ANSI) standard.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="dddf8-104">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="dddf8-104">UI element list</span></span>  
 <span data-ttu-id="dddf8-105">**SET ANSI_DEFAULTS**</span><span class="sxs-lookup"><span data-stu-id="dddf8-105">**SET ANSI_DEFAULTS**</span></span>  
 <span data-ttu-id="dddf8-106">既定の ISO 設定をすべて選択します。</span><span class="sxs-lookup"><span data-stu-id="dddf8-106">Select all of the default ISO settings.</span></span> <span data-ttu-id="dddf8-107">このボックスは ISO 設定の一部だけを構成するので、既定では使用できません。</span><span class="sxs-lookup"><span data-stu-id="dddf8-107">This box is unavailable by default, because only some of the ISO settings are configured.</span></span>  
  
 <span data-ttu-id="dddf8-108">**SET QUOTED_IDENTIFIER**</span><span class="sxs-lookup"><span data-stu-id="dddf8-108">**SET QUOTED_IDENTIFIER**</span></span>  
 <span data-ttu-id="dddf8-109">オブジェクト識別子を引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="dddf8-109">Surround object identifiers with quotation marks.</span></span> <span data-ttu-id="dddf8-110">既定では、このオプションはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="dddf8-110">This option is selected by default.</span></span>  
  
 <span data-ttu-id="dddf8-111">**SET ANSI_NULL_DFLT_ON**</span><span class="sxs-lookup"><span data-stu-id="dddf8-111">**SET ANSI_NULL_DFLT_ON**</span></span>  
 <span data-ttu-id="dddf8-112">CREATE TABLE または ALTER TABLE ステートメントの実行中に、NOT NULL が明示的に定義されていないすべてのユーザー定義データ型または列に対して、NULL 値を許容します (既定の状態)。</span><span class="sxs-lookup"><span data-stu-id="dddf8-112">Allow null values for all user-defined data types or columns that are not explicitly defined as NOTNULL during a CREATE TABLE or ALTER TABLE statement (the default state).</span></span> <span data-ttu-id="dddf8-113">既定では、このオプションはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="dddf8-113">This option is selected by default.</span></span>  
  
 <span data-ttu-id="dddf8-114">**[SET IMPLICIT_TRANSACTIONS]**</span><span class="sxs-lookup"><span data-stu-id="dddf8-114">**SET IMPLICIT_TRANSACTIONS**</span></span>  
 <span data-ttu-id="dddf8-115">既定では、このオプションはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="dddf8-115">This option is not selected by default.</span></span>  
  
 <span data-ttu-id="dddf8-116">**SET CURSOR_CLOSE_ON_COMMIT**</span><span class="sxs-lookup"><span data-stu-id="dddf8-116">**SET CURSOR_CLOSE_ON_COMMIT**</span></span>  
 <span data-ttu-id="dddf8-117">トランザクションがコミットされたときに開いているカーソルを自動的に閉じます (ISO に準拠)。</span><span class="sxs-lookup"><span data-stu-id="dddf8-117">Close any open cursors automatically (in compliance with ISO) when a transaction is committed.</span></span> <span data-ttu-id="dddf8-118">この値がオフに設定されている場合、トランザクションが変わってもカーソルは開いたままです。接続が終了するか、カーソルが明示的に閉じるときだけカーソルが閉じます。</span><span class="sxs-lookup"><span data-stu-id="dddf8-118">When cleared (set to OFF), cursors remain open across transaction boundaries, closing only when the connection is closed or when they are explicitly closed.</span></span> <span data-ttu-id="dddf8-119">既定では、このオプションはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="dddf8-119">This option is not selected by default.</span></span>  
  
 <span data-ttu-id="dddf8-120">**SET ANSI_PADDING**</span><span class="sxs-lookup"><span data-stu-id="dddf8-120">**SET ANSI_PADDING**</span></span>  
 <span data-ttu-id="dddf8-121">列の定義されたサイズよりも短い値を列に格納する方法、および**char**、 **varchar**、 **binary**、 **varbinary**データの末尾に空白がある値を列に格納する方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="dddf8-121">Controls the way the column stores values shorter than the defined size of the column, and the way the column stores values that have trailing blanks in **char**, **varchar**, **binary**, and **varbinary** data.</span></span> <span data-ttu-id="dddf8-122">この設定は新しい列の定義にだけ影響します。</span><span class="sxs-lookup"><span data-stu-id="dddf8-122">This setting affects only the definition of new columns.</span></span> <span data-ttu-id="dddf8-123">列が作成された後は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では列の作成時の設定に基づいて値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="dddf8-123">After the column is created, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stores the values based on the setting when the column was created.</span></span> <span data-ttu-id="dddf8-124">この設定を後で変更しても、既存の列には影響がありません。</span><span class="sxs-lookup"><span data-stu-id="dddf8-124">Existing columns are not affected by a later change to this setting.</span></span> <span data-ttu-id="dddf8-125">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="dddf8-125">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="dddf8-126">**SET ANSI_WARNINGS**</span><span class="sxs-lookup"><span data-stu-id="dddf8-126">**SET ANSI_WARNINGS**</span></span>  
 <span data-ttu-id="dddf8-127">複数のエラー条件に対して ISO 標準の動作をすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="dddf8-127">Specifies ISO standard behavior for several error conditions:</span></span>  
  
-   <span data-ttu-id="dddf8-128">このチェック ボックスをオンにすると、NULL 値が集計関数 (SUM、AVG、MAX、MIN、STDEV、STDEVP、VAR、VARP、COUNT など) で使用されている場合に、警告メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="dddf8-128">When this check box is selected, if null values appear in aggregate functions (such as SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP, or COUNT), a warning message is generated.</span></span> <span data-ttu-id="dddf8-129">**オフ**の場合は、警告メッセージは生成されません。</span><span class="sxs-lookup"><span data-stu-id="dddf8-129">When **OFF**, no warning is issued.</span></span>  
  
-   <span data-ttu-id="dddf8-130">このチェック ボックスをオフにすると、0 除算や演算オーバーフロー エラーが発生したときにステートメントがロールバックされ、エラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="dddf8-130">When this check box is cleared, divide-by-zero and arithmetic overflow errors cause the statement to be rolled back and an error message is generated.</span></span> <span data-ttu-id="dddf8-131">オフの場合は、0 除算や演算オーバーフロー エラーが発生したときに NULL 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="dddf8-131">When OFF, divide-by-zero and arithmetic overflow errors cause null values to be returned.</span></span> <span data-ttu-id="dddf8-132">INSERT 処理または UPDATE 処理が character、Unicode、または binary 型の列に対して実行され、新しい値が列の最大サイズより長くなると、0 除算や演算オーバーフロー エラーが原因となって NULL 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="dddf8-132">The behavior in which a divide-by-zero or arithmetic overflow error causes null values to be returned occurs if an INSERTor UPDATEoperation is attempted on a character, Unicode, or binary column in which the length of a new value exceeds the maximum size of the column.</span></span> <span data-ttu-id="dddf8-133">**SET ANSI_WARNINGS**が ON の場合、挿入または更新操作は ISO 標準で指定されているとおりにキャンセルされます。</span><span class="sxs-lookup"><span data-stu-id="dddf8-133">If **SET ANSI_WARNINGS** is ON, the INSERT or UPDATE operation is canceled as specified by the ISO standard.</span></span> <span data-ttu-id="dddf8-134">文字型の列の後続の空白とバイナリ列の後続の NULL は無視されます。</span><span class="sxs-lookup"><span data-stu-id="dddf8-134">Trailing blanks are ignored for character columns, and trailing nulls are ignored for binary columns.</span></span> <span data-ttu-id="dddf8-135">OFF の場合、データは列のサイズに切り捨てられ、ステートメントは成功します。</span><span class="sxs-lookup"><span data-stu-id="dddf8-135">When OFF, data is truncated to the size of the column and the statement succeeds.</span></span>  
  
 <span data-ttu-id="dddf8-136">既定では、このオプションはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="dddf8-136">This option is selected by default.</span></span>  
  
 <span data-ttu-id="dddf8-137">**SET ANSI_NULLS**</span><span class="sxs-lookup"><span data-stu-id="dddf8-137">**SET ANSI_NULLS**</span></span>  
 <span data-ttu-id="dddf8-138">`=`(等号) 比較演算子と`<>`(不等号) 比較演算子を NULL 値に対して使用した場合に ISO に準拠した動作をすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="dddf8-138">Specifies ISO compliant behavior of the Equal (`=`) and Not Equal to (`<>`) comparison operators when used with null values.</span></span> <span data-ttu-id="dddf8-139">**[SET ANSI_NULLS]** がオンの場合、NULL 値に対する比較はすべて UNKNOWN として評価されます。これは ISO に準拠した動作です。</span><span class="sxs-lookup"><span data-stu-id="dddf8-139">When **SET ANSI_NULLS** is selected, all comparisons against a null value evaluate to UNKNOWN, the ISO compliant behavior.</span></span> <span data-ttu-id="dddf8-140">**[SET ANSI_NULLS]** がオフの場合、データ値が NULL であれば、NULL 値に対するデータの比較はすべて TRUE に評価されます。</span><span class="sxs-lookup"><span data-stu-id="dddf8-140">When **SET ANSI_NULLS** is not selected, comparisons of all data against a null value evaluate to TRUE if the data value is NULL.</span></span> <span data-ttu-id="dddf8-141">既定では、このオプションはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="dddf8-141">This option is selected by default.</span></span>  
  
 <span data-ttu-id="dddf8-142">**既定値にリセット**</span><span class="sxs-lookup"><span data-stu-id="dddf8-142">**Reset to Default**</span></span>  
 <span data-ttu-id="dddf8-143">このページ上のすべての値を元の既定値にリセットします。</span><span class="sxs-lookup"><span data-stu-id="dddf8-143">Resets all values on this page to the original default values.</span></span>  
  
  
