---
title: MSSQLSERVER_102 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 102 (Database Engine error)
ms.assetid: 264dc1a2-c8a0-4c89-b5f6-951baf950299
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 18c330b8d6a534ca11e2ad2c03f89793f8c832e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632001"
---
# <a name="mssqlserver_102"></a><span data-ttu-id="ce6a2-102">MSSQLSERVER_102</span><span class="sxs-lookup"><span data-stu-id="ce6a2-102">MSSQLSERVER_102</span></span>
    
## <a name="details"></a><span data-ttu-id="ce6a2-103">詳細</span><span class="sxs-lookup"><span data-stu-id="ce6a2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce6a2-104">製品名</span><span class="sxs-lookup"><span data-stu-id="ce6a2-104">Product Name</span></span>|<span data-ttu-id="ce6a2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ce6a2-105">SQL Server</span></span>|  
|<span data-ttu-id="ce6a2-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="ce6a2-106">Event ID</span></span>|<span data-ttu-id="ce6a2-107">102</span><span class="sxs-lookup"><span data-stu-id="ce6a2-107">102</span></span>|  
|<span data-ttu-id="ce6a2-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="ce6a2-108">Event Source</span></span>|<span data-ttu-id="ce6a2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ce6a2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ce6a2-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ce6a2-110">Component</span></span>|<span data-ttu-id="ce6a2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ce6a2-111">SQLEngine</span></span>|  
|<span data-ttu-id="ce6a2-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="ce6a2-112">Symbolic Name</span></span>|<span data-ttu-id="ce6a2-113">P_SYNTAXERR2</span><span class="sxs-lookup"><span data-stu-id="ce6a2-113">P_SYNTAXERR2</span></span>|  
|<span data-ttu-id="ce6a2-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="ce6a2-114">Message Text</span></span>|<span data-ttu-id="ce6a2-115">'%.\*ls' 付近に不適切な構文があります。</span><span class="sxs-lookup"><span data-stu-id="ce6a2-115">Incorrect syntax near '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ce6a2-116">説明</span><span class="sxs-lookup"><span data-stu-id="ce6a2-116">Explanation</span></span>  
 <span data-ttu-id="ce6a2-117">構文エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="ce6a2-117">Indicates a syntax error.</span></span> <span data-ttu-id="ce6a2-118">エラーにより[!INCLUDE[ssDE](../../includes/ssde-md.md)]でステートメントを処理できないため、追加情報は入手できません。</span><span class="sxs-lookup"><span data-stu-id="ce6a2-118">Additional information is not available because the error prevents the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from processing the statement.</span></span>  
  
 <span data-ttu-id="ce6a2-119">このエラーは、互換性モードが 90 でも 100 でもない場合に、非推奨の RC4 暗号化または RC4_128 暗号化を使用して対称キーを作成しようとして発生した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ce6a2-119">Can be caused by attempting to create a symmetric key using the deprecated RC4 or RC4_128 encryption, when not in 90 or 100 compatibility mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ce6a2-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="ce6a2-120">User Action</span></span>  
 <span data-ttu-id="ce6a2-121">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに構文エラーがないか調べてください。</span><span class="sxs-lookup"><span data-stu-id="ce6a2-121">Search the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement for syntax errors.</span></span>  
  
 <span data-ttu-id="ce6a2-122">RC4 または RC4_128 を使用して対称キーを作成する場合、AES アルゴリズムのいずれかなど、新しい暗号化を選択します</span><span class="sxs-lookup"><span data-stu-id="ce6a2-122">If creating a symmetric key using the RC4 or RC4_128, select a newer encryption such as one of the AES algorithms.</span></span> <span data-ttu-id="ce6a2-123">(推奨)。RC4 を使用する必要がある場合、ALTER DATABASE SET COMPATIBILITY_LEVEL を使用して、データベースの互換性レベルを 90 または 100 に設定します</span><span class="sxs-lookup"><span data-stu-id="ce6a2-123">(Recommended.) If you must use RC4, use ALTER DATABASE SET COMPATIBILITY_LEVEL to set the database to compatibility level 90 or 100.</span></span> <span data-ttu-id="ce6a2-124">(非推奨)。</span><span class="sxs-lookup"><span data-stu-id="ce6a2-124">(Not recommended.)</span></span>  
  
  
