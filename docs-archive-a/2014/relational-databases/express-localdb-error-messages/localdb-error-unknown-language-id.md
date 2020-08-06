---
title: LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: fa082dca-bf88-46e7-b61e-7ac8835a3493
author: stevestein
ms.author: sstein
ms.openlocfilehash: e71f7b443a1999a5edbb17dc11ee4d578834faf4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642089"
---
# <a name="localdb_error_unknown_language_id"></a><span data-ttu-id="8bb37-102">LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID</span><span class="sxs-lookup"><span data-stu-id="8bb37-102">LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID</span></span>
    
## <a name="details"></a><span data-ttu-id="8bb37-103">詳細</span><span class="sxs-lookup"><span data-stu-id="8bb37-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8bb37-104">製品名</span><span class="sxs-lookup"><span data-stu-id="8bb37-104">Product Name</span></span>|<span data-ttu-id="8bb37-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8bb37-105">SQL Server</span></span>|  
|<span data-ttu-id="8bb37-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8bb37-106">Event ID</span></span>|<span data-ttu-id="8bb37-107">270</span><span class="sxs-lookup"><span data-stu-id="8bb37-107">270</span></span>|  
|<span data-ttu-id="8bb37-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="8bb37-108">Event Source</span></span>|<span data-ttu-id="8bb37-109">SQL Server Local Database Runtime 12.0</span><span class="sxs-lookup"><span data-stu-id="8bb37-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="8bb37-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8bb37-110">Component</span></span>|<span data-ttu-id="8bb37-111">Local Database Runtime API</span><span class="sxs-lookup"><span data-stu-id="8bb37-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="8bb37-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="8bb37-112">Message Text</span></span>|<span data-ttu-id="8bb37-113">ローカライズされたエラー メッセージの取得中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8bb37-113">Error getting the localized error message.</span></span> <span data-ttu-id="8bb37-114">'Language ID' パラメーターで指定された言語が不明です。</span><span class="sxs-lookup"><span data-stu-id="8bb37-114">The language specified by 'Language ID' parameter is unknown.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8bb37-115">説明</span><span class="sxs-lookup"><span data-stu-id="8bb37-115">Explanation</span></span>  
 <span data-ttu-id="8bb37-116">Local Database Runtime のエラー メッセージ用に要求した言語が不明であるか、サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8bb37-116">The requested language for the Local Database Runtime error message is unknown or not supported.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8bb37-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8bb37-117">User Action</span></span>  
 <span data-ttu-id="8bb37-118">Local Database Runtime のエラー メッセージ用にサポートされている言語の 1 つまたは既定の言語を要求してください。</span><span class="sxs-lookup"><span data-stu-id="8bb37-118">Try requesting one of the supported languages for Local Database Runtime error messages, or a default language.</span></span>  
  
  
