---
title: MSSQLSERVER_107 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 107 (Database Engine error)
ms.assetid: f33f514c-56aa-42e2-841b-e91244da90e2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b9388bbda6f00b1aafd02caee1b6a7b8387564f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643407"
---
# <a name="mssqlserver_107"></a><span data-ttu-id="e74f3-102">MSSQLSERVER_107</span><span class="sxs-lookup"><span data-stu-id="e74f3-102">MSSQLSERVER_107</span></span>
    
## <a name="details"></a><span data-ttu-id="e74f3-103">詳細</span><span class="sxs-lookup"><span data-stu-id="e74f3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e74f3-104">製品名</span><span class="sxs-lookup"><span data-stu-id="e74f3-104">Product Name</span></span>|<span data-ttu-id="e74f3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e74f3-105">SQL Server</span></span>|  
|<span data-ttu-id="e74f3-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e74f3-106">Event ID</span></span>|<span data-ttu-id="e74f3-107">107</span><span class="sxs-lookup"><span data-stu-id="e74f3-107">107</span></span>|  
|<span data-ttu-id="e74f3-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="e74f3-108">Event Source</span></span>|<span data-ttu-id="e74f3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e74f3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e74f3-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e74f3-110">Component</span></span>|<span data-ttu-id="e74f3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e74f3-111">SQLEngine</span></span>|  
|<span data-ttu-id="e74f3-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="e74f3-112">Symbolic Name</span></span>|<span data-ttu-id="e74f3-113">P_NOCORRMATCH</span><span class="sxs-lookup"><span data-stu-id="e74f3-113">P_NOCORRMATCH</span></span>|  
|<span data-ttu-id="e74f3-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="e74f3-114">Message Text</span></span>|<span data-ttu-id="e74f3-115">列プレフィックス '%.\*ls' とクエリで使用されているテーブル名または別名が一致しません。</span><span class="sxs-lookup"><span data-stu-id="e74f3-115">The column prefix '%.\*ls' does not match with a table name or alias name used in the query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e74f3-116">説明</span><span class="sxs-lookup"><span data-stu-id="e74f3-116">Explanation</span></span>  
 <span data-ttu-id="e74f3-117">クエリの選択リストに、不適切な列プレフィックスで修飾されたアスタリスク (\*) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e74f3-117">The select list of the query contains an asterisk (\*) that is incorrectly qualified with a column prefix.</span></span> <span data-ttu-id="e74f3-118">このエラーは、次のような状況で返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e74f3-118">This error can be returned under the following conditions:</span></span>  
  
-   <span data-ttu-id="e74f3-119">列プレフィックス '%.\*ls' とクエリで使用されているテーブル名または別名が一致しない。</span><span class="sxs-lookup"><span data-stu-id="e74f3-119">The column prefix does not correspond to any table or alias name used in the query.</span></span> <span data-ttu-id="e74f3-120">たとえば、次のステートメントでは、FROM 句で定義していない別名 (`T1`) を列プレフィックスとして使用しています。</span><span class="sxs-lookup"><span data-stu-id="e74f3-120">For example, the following statement uses an alias name (`T1`) as a column prefix, but the alias is not defined in the FROM clause.</span></span>  
  
    ```  
    SELECT T1.* FROM dbo.ErrorLog;  
    ```  
  
-   <span data-ttu-id="e74f3-121">FROM 句でテーブルの別名を指定しているときに、テーブル名を列プレフィックスとして指定している。</span><span class="sxs-lookup"><span data-stu-id="e74f3-121">A table name is specified as a column prefix when an alias name for the table is supplied in the FROM clause.</span></span> <span data-ttu-id="e74f3-122">たとえば、次のステートメントでは、FROM 句でテーブルの別名 (`ErrorLog`) を定義しているにもかかわらず、テーブル名 `T1` を列プレフィックスとして使用しています。</span><span class="sxs-lookup"><span data-stu-id="e74f3-122">For example, the following statement uses the table name `ErrorLog` as the column prefix; however, the table has an alias (`T1`) defined in the FROM clause.</span></span>  
  
    ```  
    SELECT ErrorLog.* FROM dbo.ErrorLog AS T1;  
    ```  
  
     <span data-ttu-id="e74f3-123">FROM 句でテーブルの別名を指定した場合、テーブルの列のプレフィックスとして使用できるのはその別名だけです。</span><span class="sxs-lookup"><span data-stu-id="e74f3-123">If an alias has been provided for a table name in the FROM clause, you can only use the alias to prefix columns from the table.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e74f3-124">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="e74f3-124">User Action</span></span>  
 <span data-ttu-id="e74f3-125">列プレフィックスとクエリの FROM 句で指定したテーブル名または別名を一致させます。</span><span class="sxs-lookup"><span data-stu-id="e74f3-125">Match the column prefixes against the table names or alias names specified in the FROM clause of the query.</span></span> <span data-ttu-id="e74f3-126">たとえば、上記のステートメントは次のように修正できます。</span><span class="sxs-lookup"><span data-stu-id="e74f3-126">For example, the statements above can be corrected as follows:</span></span>  
  
```  
SELECT T1.* FROM dbo.ErrorLog AS T1;  
```  
  
 <span data-ttu-id="e74f3-127">or</span><span class="sxs-lookup"><span data-stu-id="e74f3-127">or</span></span>  
  
```  
SELECT ErrorLog.* FROM dbo.ErrorLog;  
```  
  
## <a name="see-also"></a><span data-ttu-id="e74f3-128">参照</span><span class="sxs-lookup"><span data-stu-id="e74f3-128">See Also</span></span>  
 [<span data-ttu-id="e74f3-129">MSSQLSERVER_4104</span><span class="sxs-lookup"><span data-stu-id="e74f3-129">MSSQLSERVER_4104</span></span>](mssqlserver-4104-database-engine-error.md)  
  
  
