---
title: MSSQLSERVER_9532 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9532 (Database Engine error)
ms.assetid: ab95cce8-4f97-4aea-a746-a73eea7c9aab
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c34ebc7c682d2ffe8bc0205565f5dfd44fdd5b66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639998"
---
# <a name="mssqlserver_9532"></a><span data-ttu-id="1b9fd-102">MSSQLSERVER_9532</span><span class="sxs-lookup"><span data-stu-id="1b9fd-102">MSSQLSERVER_9532</span></span>
    
## <a name="details"></a><span data-ttu-id="1b9fd-103">詳細</span><span class="sxs-lookup"><span data-stu-id="1b9fd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1b9fd-104">製品名</span><span class="sxs-lookup"><span data-stu-id="1b9fd-104">Product Name</span></span>|<span data-ttu-id="1b9fd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1b9fd-105">SQL Server</span></span>|  
|<span data-ttu-id="1b9fd-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="1b9fd-106">Event ID</span></span>|<span data-ttu-id="1b9fd-107">9532</span><span class="sxs-lookup"><span data-stu-id="1b9fd-107">9532</span></span>|  
|<span data-ttu-id="1b9fd-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="1b9fd-108">Event Source</span></span>|<span data-ttu-id="1b9fd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1b9fd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1b9fd-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1b9fd-110">Component</span></span>|<span data-ttu-id="1b9fd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1b9fd-111">SQLEngine</span></span>|  
|<span data-ttu-id="1b9fd-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="1b9fd-112">Symbolic Name</span></span>|<span data-ttu-id="1b9fd-113">XMLERR_COLUMNSET_CANNOT_CONVERT_FROM_TO</span><span class="sxs-lookup"><span data-stu-id="1b9fd-113">XMLERR_COLUMNSET_CANNOT_CONVERT_FROM_TO</span></span>|  
|<span data-ttu-id="1b9fd-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="1b9fd-114">Message Text</span></span>|<span data-ttu-id="1b9fd-115">列セット '%.\*ls' に関係するクエリ/DML 操作で、列 '%.\*ls' のデータ型 '%ls' をデータ型 '%ls' に変換する際に変換に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="1b9fd-115">In the query/DML operation involving  column set '%.\*ls', conversion failed when converting from the data type '%ls' to the data type '%ls' for the column '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1b9fd-116">説明</span><span class="sxs-lookup"><span data-stu-id="1b9fd-116">Explanation</span></span>  
 <span data-ttu-id="1b9fd-117">列セットは、型指定されていない XML 表現であり、テーブルの複数の列を 1 つにまとめて構造化した出力です。</span><span class="sxs-lookup"><span data-stu-id="1b9fd-117">A column set is an untyped XML representation that combines some of the columns of a table into a structured output.</span></span> <span data-ttu-id="1b9fd-118">XML 列セットを使用してスパース列の値を挿入または更新する場合、基になるスパース列に挿入される値は、`xml` データ型から暗黙的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="1b9fd-118">When you are inserting or updating sparse column values through the XML column set, the values that are inserted into the underlying sparse columns are implicitly converted from the `xml` data type.</span></span> <span data-ttu-id="1b9fd-119">列のデータ型に変換できない値が指定されました。</span><span class="sxs-lookup"><span data-stu-id="1b9fd-119">A value was provided that cannot be converted to the data type of the column.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1b9fd-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="1b9fd-120">User Action</span></span>  
 <span data-ttu-id="1b9fd-121">指定された値は暗黙的に変換することができなかったため、無効なエントリとなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1b9fd-121">Because the value provided could not be implicitly converted, it might be an invalid entry.</span></span> <span data-ttu-id="1b9fd-122">エラーを修正して再試行してください。</span><span class="sxs-lookup"><span data-stu-id="1b9fd-122">Correct the error and retry.</span></span> <span data-ttu-id="1b9fd-123">値が正しい場合は、列セットではなく個々の列を使用するようにステートメントを変更します。</span><span class="sxs-lookup"><span data-stu-id="1b9fd-123">If the value is correct, modify the statement to use the individual columns instead of the column set.</span></span> <span data-ttu-id="1b9fd-124">これにより、値を適切なデータ型に明示的にキャストすることができます。</span><span class="sxs-lookup"><span data-stu-id="1b9fd-124">This will allow you to explicitly cast the value into the correct data type.</span></span>  
  
  
