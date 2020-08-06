---
title: アップグレード後に、予約された新しいキーワードを識別子として使用することはできません |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- keywords [SQL Server], after upgrade
- keywords [SQL Server], reserved
- keywords [SQL Server]
ms.assetid: cb242081-54f8-4273-a8ef-52f3751c25ef
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 36f7f8cadcba5e114feee4a3c42de6f40070ce72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640500"
---
# <a name="after-upgrade-new-reserved-keywords-cannot-be-used-as-identifiers"></a><span data-ttu-id="d06dc-102">アップグレード後に、予約された新しいキーワードを識別子として使用できない</span><span class="sxs-lookup"><span data-stu-id="d06dc-102">After upgrade, new reserved keywords cannot be used as identifiers</span></span>
  <span data-ttu-id="d06dc-103">アップグレード アドバイザーは、予約されたキーワードとして使用されている単語を検出しました。</span><span class="sxs-lookup"><span data-stu-id="d06dc-103">Upgrade Advisor detected the use of words that are reserved keywords.</span></span> <span data-ttu-id="d06dc-104">予約されたキーワードは、名前を区切らない限り、識別子またはオブジェクトの名前として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d06dc-104">A reserved keyword cannot be used as an identifier or object name unless the name is delimited.</span></span>  
  
## <a name="component"></a><span data-ttu-id="d06dc-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d06dc-105">Component</span></span>  
 <span data-ttu-id="d06dc-106">データベース エンジン</span><span class="sxs-lookup"><span data-stu-id="d06dc-106">Database Engine</span></span>  
  
## <a name="description"></a><span data-ttu-id="d06dc-107">説明</span><span class="sxs-lookup"><span data-stu-id="d06dc-107">Description</span></span>  
 <span data-ttu-id="d06dc-108">互換性レベル 90 以下では、次の単語は予約されたキーワードではなく、[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト内で識別子またはオブジェクトの名前として使用できます。</span><span class="sxs-lookup"><span data-stu-id="d06dc-108">At compatibility level 90 or lower, the following words are not reserved keywords and can be used as identifiers or object names in [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="d06dc-109">互換性レベル 100 では、これらの単語は完全に予約されたキーワードで、識別子またはオブジェクトの名前として使用できません。</span><span class="sxs-lookup"><span data-stu-id="d06dc-109">At compatibility level 100, these words are fully reserved keywords and should not be used as identifiers or object names.</span></span>  
  
-   <span data-ttu-id="d06dc-110">EXTERNAL</span><span class="sxs-lookup"><span data-stu-id="d06dc-110">EXTERNAL</span></span>  
  
-   <span data-ttu-id="d06dc-111">MERGE</span><span class="sxs-lookup"><span data-stu-id="d06dc-111">MERGE</span></span>  
  
-   <span data-ttu-id="d06dc-112">PIVOT</span><span class="sxs-lookup"><span data-stu-id="d06dc-112">PIVOT</span></span>  
  
-   <span data-ttu-id="d06dc-113">REVERT</span><span class="sxs-lookup"><span data-stu-id="d06dc-113">REVERT</span></span>  
  
-   <span data-ttu-id="d06dc-114">STOPLIST</span><span class="sxs-lookup"><span data-stu-id="d06dc-114">STOPLIST</span></span>  
  
-   <span data-ttu-id="d06dc-115">TABLESAMPLE</span><span class="sxs-lookup"><span data-stu-id="d06dc-115">TABLESAMPLE</span></span>  
  
-   <span data-ttu-id="d06dc-116">UNPIVOT</span><span class="sxs-lookup"><span data-stu-id="d06dc-116">UNPIVOT</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="d06dc-117">修正措置</span><span class="sxs-lookup"><span data-stu-id="d06dc-117">Corrective Action</span></span>  
 <span data-ttu-id="d06dc-118">オブジェクトの名前を変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d06dc-118">We recommend that you rename the object.</span></span> <span data-ttu-id="d06dc-119">アップグレードの前にオブジェクトの名前を変更できない場合は、名前を変更できるまで、次のいずれかの方法を使用してください。</span><span class="sxs-lookup"><span data-stu-id="d06dc-119">If that cannot be done before upgrading, use one of the following methods until the name can be changed:</span></span>  
  
-   <span data-ttu-id="d06dc-120">データベース互換性レベルの設定を 90 以下に保持します。</span><span class="sxs-lookup"><span data-stu-id="d06dc-120">Retain the database compatibility level setting of 90 or lower.</span></span>  
  
-   <span data-ttu-id="d06dc-121">区切られた識別子を使用して、オブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="d06dc-121">Refer to the object by using delimited identifiers.</span></span> <span data-ttu-id="d06dc-122">たとえば、ステートメントでは、 `CREATE TABLE [MERGE] ([MERGE] int);` 角かっこを使用して、オブジェクト名の MERGE を区切ります。</span><span class="sxs-lookup"><span data-stu-id="d06dc-122">For example, the statement `CREATE TABLE [MERGE] ([MERGE] int);` uses brackets to delimit the object name MERGE.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="d06dc-123">外部リソース</span><span class="sxs-lookup"><span data-stu-id="d06dc-123">External Resources</span></span>  
 [<span data-ttu-id="d06dc-124">予約済みキーワード &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d06dc-124">Reserved Keywords &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reserved-keywords-transact-sql)  
  
 [<span data-ttu-id="d06dc-125">MERGE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d06dc-125">MERGE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/merge-transact-sql)  
  
 [<span data-ttu-id="d06dc-126">区切られた識別子 (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="d06dc-126">Delimited Identifiers (Database Engine)</span></span>](https://go.microsoft.com/fwlink/?LinkId=112509)  
  
 [<span data-ttu-id="d06dc-127">ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d06dc-127">ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
