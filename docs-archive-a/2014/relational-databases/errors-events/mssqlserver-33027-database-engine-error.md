---
title: MSSQLSERVER_33027 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f6bb461b42b66368224fffd2c14f9b4da61abf5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640024"
---
# <a name="mssqlserver_33027"></a><span data-ttu-id="66070-102">MSSQLSERVER_33027</span><span class="sxs-lookup"><span data-stu-id="66070-102">MSSQLSERVER_33027</span></span>
    
## <a name="details"></a><span data-ttu-id="66070-103">詳細</span><span class="sxs-lookup"><span data-stu-id="66070-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="66070-104">製品名</span><span class="sxs-lookup"><span data-stu-id="66070-104">Product Name</span></span>|<span data-ttu-id="66070-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="66070-105">SQL Server</span></span>|  
|<span data-ttu-id="66070-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="66070-106">Event ID</span></span>|<span data-ttu-id="66070-107">33027</span><span class="sxs-lookup"><span data-stu-id="66070-107">33027</span></span>|  
|<span data-ttu-id="66070-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="66070-108">Event Source</span></span>|<span data-ttu-id="66070-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="66070-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="66070-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="66070-110">Component</span></span>|<span data-ttu-id="66070-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="66070-111">SQLEngine</span></span>|  
|<span data-ttu-id="66070-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="66070-112">Symbolic Name</span></span>|<span data-ttu-id="66070-113">SEC_CRYPTOPROV_CANTLOADDLL</span><span class="sxs-lookup"><span data-stu-id="66070-113">SEC_CRYPTOPROV_CANTLOADDLL</span></span>|  
|<span data-ttu-id="66070-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="66070-114">Message Text</span></span>|<span data-ttu-id="66070-115">Authenticode 署名またはファイル パスが無効なため、暗号プロバイダー '%.\*ls' を読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="66070-115">Failed to load cryptographic provider '%.\*ls' due to an invalid Authenticode signature or invalid file path.</span></span> <span data-ttu-id="66070-116">前のメッセージでその他のエラーを確認してください。</span><span class="sxs-lookup"><span data-stu-id="66070-116">Check previous messages for other failures.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="66070-117">説明</span><span class="sxs-lookup"><span data-stu-id="66070-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="66070-118">は、エラー メッセージに表示されている暗号化サービス プロバイダーを使用できませんでした。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が該当する DLL を読み込めなかったことが原因です。</span><span class="sxs-lookup"><span data-stu-id="66070-118">was unable to use the cryptographic provider listed in the error message, because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] could not load the DLL.</span></span> <span data-ttu-id="66070-119">名前が無効であるか、Authenticode 署名が無効です。</span><span class="sxs-lookup"><span data-stu-id="66070-119">Either the name is invalid or the Authenticode signature is invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="66070-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="66070-120">User Action</span></span>  
 <span data-ttu-id="66070-121">このファイルが存在し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がファイルの場所にアクセスするための権限を持っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="66070-121">Check that the file is present and that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has permission to access that location.</span></span> <span data-ttu-id="66070-122">エラー ログで、その他の関連メッセージを確認します。</span><span class="sxs-lookup"><span data-stu-id="66070-122">Check the error log for additional related messages.</span></span> <span data-ttu-id="66070-123">または、暗号化サービス プロバイダーに詳細を問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="66070-123">Otherwise, contact the cryptographic provider for more information.</span></span>  
  
  
