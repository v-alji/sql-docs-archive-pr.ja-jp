---
title: LOCALDB_ERROR_INSUFFICIENT_BUFFER |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: ff67bda8-7e5c-4b06-8d7b-9985b6059a98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 934683cfca1a9a9c0596071824c21a0045e6ebab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645092"
---
# <a name="localdb_error_insufficient_buffer"></a><span data-ttu-id="96fb0-102">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="96fb0-102">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>
    
## <a name="details"></a><span data-ttu-id="96fb0-103">詳細</span><span class="sxs-lookup"><span data-stu-id="96fb0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="96fb0-104">製品名</span><span class="sxs-lookup"><span data-stu-id="96fb0-104">Product Name</span></span>|<span data-ttu-id="96fb0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="96fb0-105">SQL Server</span></span>|  
|<span data-ttu-id="96fb0-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="96fb0-106">Event ID</span></span>|<span data-ttu-id="96fb0-107">276</span><span class="sxs-lookup"><span data-stu-id="96fb0-107">276</span></span>|  
|<span data-ttu-id="96fb0-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="96fb0-108">Event Source</span></span>|<span data-ttu-id="96fb0-109">SQL Server Local Database Runtime 12.0</span><span class="sxs-lookup"><span data-stu-id="96fb0-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="96fb0-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="96fb0-110">Component</span></span>|<span data-ttu-id="96fb0-111">Local Database Runtime API</span><span class="sxs-lookup"><span data-stu-id="96fb0-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="96fb0-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="96fb0-112">Message Text</span></span>|<span data-ttu-id="96fb0-113">ローカル データベース インスタンスの API メソッドに渡されたバッファーのサイズが不十分です。</span><span class="sxs-lookup"><span data-stu-id="96fb0-113">The buffer passed to the Local Database instance API method has insufficient size.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="96fb0-114">説明</span><span class="sxs-lookup"><span data-stu-id="96fb0-114">Explanation</span></span>  
 <span data-ttu-id="96fb0-115">入力バッファーが短かすぎますが、切り捨ては要求されませんでした。</span><span class="sxs-lookup"><span data-stu-id="96fb0-115">The input buffer is too short, and truncation was not requested.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="96fb0-116">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="96fb0-116">User Action</span></span>  
 <span data-ttu-id="96fb0-117">指定したサイズのバッファーを提供してください。</span><span class="sxs-lookup"><span data-stu-id="96fb0-117">Provide a buffer of the specified size.</span></span>  
  
  
