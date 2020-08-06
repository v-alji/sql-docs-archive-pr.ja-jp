---
title: MSSQLSERVER_611 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f0caa1c218e8b80059c0c97aac652da7db870af3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645114"
---
# <a name="mssqlserver_611"></a><span data-ttu-id="0a7e5-102">MSSQLSERVER_611</span><span class="sxs-lookup"><span data-stu-id="0a7e5-102">MSSQLSERVER_611</span></span>
    
## <a name="details"></a><span data-ttu-id="0a7e5-103">詳細</span><span class="sxs-lookup"><span data-stu-id="0a7e5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0a7e5-104">製品名</span><span class="sxs-lookup"><span data-stu-id="0a7e5-104">Product Name</span></span>|<span data-ttu-id="0a7e5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0a7e5-105">SQL Server</span></span>|  
|<span data-ttu-id="0a7e5-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="0a7e5-106">Event ID</span></span>|<span data-ttu-id="0a7e5-107">611</span><span class="sxs-lookup"><span data-stu-id="0a7e5-107">611</span></span>|  
|<span data-ttu-id="0a7e5-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="0a7e5-108">Event Source</span></span>|<span data-ttu-id="0a7e5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0a7e5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0a7e5-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="0a7e5-110">Component</span></span>|<span data-ttu-id="0a7e5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0a7e5-111">SQLEngine</span></span>|  
|<span data-ttu-id="0a7e5-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="0a7e5-112">Symbolic Name</span></span>|<span data-ttu-id="0a7e5-113">VAR_SIZE_TOO_BIG</span><span class="sxs-lookup"><span data-stu-id="0a7e5-113">VAR_SIZE_TOO_BIG</span></span>|  
|<span data-ttu-id="0a7e5-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="0a7e5-114">Message Text</span></span>|<span data-ttu-id="0a7e5-115">行を挿入または更新できません。オーバーヘッドを含む、変数列の合計サイズが、制限を超える %d バイトです。</span><span class="sxs-lookup"><span data-stu-id="0a7e5-115">Cannot insert or update a row because total variable column size, including overhead, is %d bytes more than the limit.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0a7e5-116">説明</span><span class="sxs-lookup"><span data-stu-id="0a7e5-116">Explanation</span></span>  
 <span data-ttu-id="0a7e5-117">最大の可変長の列サイズがスキーマで許可されている値を超えています。</span><span class="sxs-lookup"><span data-stu-id="0a7e5-117">The maximum variable column size is more than that allowed by the schema.</span></span> <span data-ttu-id="0a7e5-118">vardecimal ストレージ形式を設定したときに可変長の列が固定値の制限を超えているか、可変長の列サイズが圧縮データ レコードの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で許可されている制限を超えていた場合に、エラー 611 が返されます。</span><span class="sxs-lookup"><span data-stu-id="0a7e5-118">Error 611 is returned when the variable column is over the limit in the fixed case when vardecimal storage format is enabled, or when the variable column size is over the limit allowed in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] for a compressed data record.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0a7e5-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="0a7e5-119">User Action</span></span>  
 <span data-ttu-id="0a7e5-120">レコードのサイズを縮小します。</span><span class="sxs-lookup"><span data-stu-id="0a7e5-120">Reduce the size of the record.</span></span>  
  
  
