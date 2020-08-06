---
title: MSSQLSERVER_12329 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 12329 (Database Engine error)
ms.assetid: 43f90287-36d5-46c2-ac91-a37202dcf6d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7576e32946ce0a453637273c449bbff20e5b6fac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641007"
---
# <a name="mssqlserver_12329"></a><span data-ttu-id="139b0-102">MSSQLSERVER_12329</span><span class="sxs-lookup"><span data-stu-id="139b0-102">MSSQLSERVER_12329</span></span>
    
## <a name="details"></a><span data-ttu-id="139b0-103">詳細</span><span class="sxs-lookup"><span data-stu-id="139b0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="139b0-104">製品名</span><span class="sxs-lookup"><span data-stu-id="139b0-104">Product Name</span></span>|<span data-ttu-id="139b0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="139b0-105">SQL Server</span></span>|  
|<span data-ttu-id="139b0-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="139b0-106">Event ID</span></span>|<span data-ttu-id="139b0-107">12329</span><span class="sxs-lookup"><span data-stu-id="139b0-107">12329</span></span>|  
|<span data-ttu-id="139b0-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="139b0-108">Event Source</span></span>|<span data-ttu-id="139b0-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="139b0-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="139b0-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="139b0-110">Component</span></span>|<span data-ttu-id="139b0-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="139b0-111">SQLEngine</span></span>|  
|<span data-ttu-id="139b0-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="139b0-112">Symbolic Name</span></span>|<span data-ttu-id="139b0-113">HK_UNSUPPORTED_NON_LATIN_CODEPAGE</span><span class="sxs-lookup"><span data-stu-id="139b0-113">HK_UNSUPPORTED_NON_LATIN_CODEPAGE</span></span>|  
|<span data-ttu-id="139b0-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="139b0-114">Message Text</span></span>|<span data-ttu-id="139b0-115">1252 以外のコード ページを含む照合順序を使用するデータ型 char(n) および varchar(n) は、*construct* ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="139b0-115">The data types char(n) and varchar(n) using a collation that has a code page other than 1252 are not supported with  *construct*.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="139b0-116">説明</span><span class="sxs-lookup"><span data-stu-id="139b0-116">Explanation</span></span>  
 <span data-ttu-id="139b0-117">1252 以外のコード ページを含む照合順序を使用するデータ型 char(n) および varchar(n) は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="139b0-117">Do not use the data types char(n) and varchar(n) using a collation that has a code page other than 1252.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="139b0-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="139b0-118">User Action</span></span>  
 <span data-ttu-id="139b0-119">このエラーが発生する可能性がある予期しない状況を次に示します。</span><span class="sxs-lookup"><span data-stu-id="139b0-119">One unexpected situation that can generate this error is:</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = 'us_english')  
```  
  
 <span data-ttu-id="139b0-120">代わりに、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="139b0-120">Use this instead:</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
```  
  
  
