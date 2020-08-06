---
title: ワイルドカードを使用したテキスト検索
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vswildcardsbuilder
helpviewer_keywords:
- searches [SQL Server Management Studio], wildcards
- Query Editor [SQL Server Management Studio], wildcard searches
- wildcard options [SQL Server Management Studio]
ms.assetid: 449600f8-cc87-4b3f-878a-59c158a88a40
author: rothja
ms.author: jroth
ms.openlocfilehash: cc4e24c3dce73e46350b0c106429c42ab5f0edb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645483"
---
# <a name="search-text-with-wildcards"></a><span data-ttu-id="3b716-102">ワイルドカードを使用したテキスト検索</span><span class="sxs-lookup"><span data-stu-id="3b716-102">Search Text with Wildcards</span></span>
  <span data-ttu-id="3b716-103">**の**[検索と置換][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ダイアログ ボックスの **[検索する文字列]** フィールドでは、文字や数字の代わりに以下の式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3b716-103">The following expressions can replace characters or digits in the **Find what** field of the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Find and Replace** dialog box.</span></span>  
  
#### <a name="to-search-using-wildcards"></a><span data-ttu-id="3b716-104">ワイルドカードを使用して検索を行うには</span><span class="sxs-lookup"><span data-stu-id="3b716-104">To search using wildcards</span></span>  
  
1.  <span data-ttu-id="3b716-105">[クイック検索]、 **[フォルダーを指定して検索]** 、 **[クイック置換]** 、 **[フォルダーを指定して置換]** の各操作に関して、 **[検索する文字列]** フィールドでのワイルドカードの使用を有効にするには、 **[検索オプション]** の下の **[条件]** をオンにして、 **[ワイルドカード]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="3b716-105">To enable the use of wildcards in the **Find what** field during Quick Find, **Find in Files**, **Quick Replace**, or **Replace in Files** operations, select the **Use** option under **Find Options** and then choose **Wildcards**.</span></span>  
  
2.  <span data-ttu-id="3b716-106">**[検索する文字列]** フィールドの横にある三角形の **参照一覧** ボタンが使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="3b716-106">The triangular **Reference List** button next to the **Find what** field then becomes available.</span></span> <span data-ttu-id="3b716-107">このボタンをクリックすると、使用可能なワイルドカードの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3b716-107">Click this button to display a list of the available wildcards.</span></span> <span data-ttu-id="3b716-108">**参照一覧**から項目を選択すると、その項目が **[検索する文字列]** の文字列に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="3b716-108">When you choose any item from the **Reference List**, it is inserted into the **Find what** string.</span></span>  
  
 <span data-ttu-id="3b716-109">**参照一覧**から使用できるワイルドカードを以下にまとめます。</span><span class="sxs-lookup"><span data-stu-id="3b716-109">The following table describes the wildcards available in the **Reference List**.</span></span>  
  
|<span data-ttu-id="3b716-110">式</span><span class="sxs-lookup"><span data-stu-id="3b716-110">Expression</span></span>|<span data-ttu-id="3b716-111">構文</span><span class="sxs-lookup"><span data-stu-id="3b716-111">Syntax</span></span>|<span data-ttu-id="3b716-112">説明</span><span class="sxs-lookup"><span data-stu-id="3b716-112">Description</span></span>|  
|----------------|------------|-----------------|  
|<span data-ttu-id="3b716-113">任意の 1 文字</span><span class="sxs-lookup"><span data-stu-id="3b716-113">Any single character</span></span>|<span data-ttu-id="3b716-114">?</span><span class="sxs-lookup"><span data-stu-id="3b716-114">?</span></span>|<span data-ttu-id="3b716-115">任意の 1 文字に相当します。</span><span class="sxs-lookup"><span data-stu-id="3b716-115">Matches any single character.</span></span>|  
|<span data-ttu-id="3b716-116">任意の 1 つの数字</span><span class="sxs-lookup"><span data-stu-id="3b716-116">Any single digit</span></span>|#|<span data-ttu-id="3b716-117">任意の 1 つの数字に相当します。</span><span class="sxs-lookup"><span data-stu-id="3b716-117">Matches any single digit.</span></span> <span data-ttu-id="3b716-118">一例として、7# は 7 とその後の 1 つの数字に相当します (たとえば、71 は一致項目ですが、17 は違います)。</span><span class="sxs-lookup"><span data-stu-id="3b716-118">For example, 7# matches numbers that include 7 followed by another number, such as 71, but not 17.</span></span>|  
|<span data-ttu-id="3b716-119">セット内以外の文字</span><span class="sxs-lookup"><span data-stu-id="3b716-119">Characters not in set</span></span>|<span data-ttu-id="3b716-120">[!</span><span class="sxs-lookup"><span data-stu-id="3b716-120">[!</span></span> <span data-ttu-id="3b716-121">]</span><span class="sxs-lookup"><span data-stu-id="3b716-121">]</span></span>|<span data-ttu-id="3b716-122">セット内に指定されていない任意の 1 文字に相当します。</span><span class="sxs-lookup"><span data-stu-id="3b716-122">Matches any one character that is not specified in the set.</span></span>|  
|<span data-ttu-id="3b716-123">1 つ以上の文字</span><span class="sxs-lookup"><span data-stu-id="3b716-123">One or more characters</span></span>|*|<span data-ttu-id="3b716-124">任意の 1 つ以上の文字に相当します。</span><span class="sxs-lookup"><span data-stu-id="3b716-124">Matches any one or more characters.</span></span> <span data-ttu-id="3b716-125">一例として、new\* は「new」を含む任意のテキスト (newfile.txt など) に相当します。</span><span class="sxs-lookup"><span data-stu-id="3b716-125">For example, new\* matches any text that includes "new", such as newfile.txt.</span></span>|  
|<span data-ttu-id="3b716-126">文字のセット</span><span class="sxs-lookup"><span data-stu-id="3b716-126">Set of characters</span></span>|<span data-ttu-id="3b716-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="3b716-127">[ ]</span></span>|<span data-ttu-id="3b716-128">セット内に指定されている任意の 1 文字に相当します。</span><span class="sxs-lookup"><span data-stu-id="3b716-128">Matches any one of the characters specified in the set.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3b716-129">参照</span><span class="sxs-lookup"><span data-stu-id="3b716-129">See Also</span></span>  
 <span data-ttu-id="3b716-130">[検索と置換](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="3b716-130">[Search and Replace](search-and-replace.md) </span></span>  
 [<span data-ttu-id="3b716-131">正規表現によるテキストの検索</span><span class="sxs-lookup"><span data-stu-id="3b716-131">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
