---
title: MSSQLSERVER_1458 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: efa45177a92402b25099be5bb3e3dcc91a5fa6d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643914"
---
# <a name="mssqlserver_1458"></a><span data-ttu-id="9c45b-102">MSSQLSERVER_1458</span><span class="sxs-lookup"><span data-stu-id="9c45b-102">MSSQLSERVER_1458</span></span>
    
## <a name="details"></a><span data-ttu-id="9c45b-103">詳細</span><span class="sxs-lookup"><span data-stu-id="9c45b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9c45b-104">製品名</span><span class="sxs-lookup"><span data-stu-id="9c45b-104">Product Name</span></span>|<span data-ttu-id="9c45b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9c45b-105">SQL Server</span></span>|  
|<span data-ttu-id="9c45b-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="9c45b-106">Event ID</span></span>|<span data-ttu-id="9c45b-107">1458</span><span class="sxs-lookup"><span data-stu-id="9c45b-107">1458</span></span>|  
|<span data-ttu-id="9c45b-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="9c45b-108">Event Source</span></span>|<span data-ttu-id="9c45b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9c45b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9c45b-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="9c45b-110">Component</span></span>|<span data-ttu-id="9c45b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9c45b-111">SQLEngine</span></span>|  
|<span data-ttu-id="9c45b-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="9c45b-112">Symbolic Name</span></span>|<span data-ttu-id="9c45b-113">DBM_FAILREDO_ON_PRIMARY</span><span class="sxs-lookup"><span data-stu-id="9c45b-113">DBM_FAILREDO_ON_PRIMARY</span></span>|  
|<span data-ttu-id="9c45b-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="9c45b-114">Message Text</span></span>|<span data-ttu-id="9c45b-115">'%.\*ls' データベースのプリンシパル コピーでエラー %d、ステータス %d、重要度 %d が発生しました。</span><span class="sxs-lookup"><span data-stu-id="9c45b-115">The principal copy of the '%.\*ls' database encountered error %d, status %d, severity %d.</span></span> <span data-ttu-id="9c45b-116">データベース ミラーリングは中断されました。</span><span class="sxs-lookup"><span data-stu-id="9c45b-116">Database mirroring has been suspended.</span></span> <span data-ttu-id="9c45b-117">エラー状態を解決して、ミラーリングを再開してください。</span><span class="sxs-lookup"><span data-stu-id="9c45b-117">Try to resolve the error condition, and resume mirroring.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9c45b-118">説明</span><span class="sxs-lookup"><span data-stu-id="9c45b-118">Explanation</span></span>  
 <span data-ttu-id="9c45b-119">このメッセージは、データベース ミラーリングを中断させるエラーがプリンシパル データベースで検出されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="9c45b-119">This messages indicates that the principal database encountered an error that caused database mirroring to be suspended.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9c45b-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="9c45b-120">User Action</span></span>  
 <span data-ttu-id="9c45b-121">このエラーはほとんどの場合、自動で修復されます。</span><span class="sxs-lookup"><span data-stu-id="9c45b-121">Most cases of this error are self correcting.</span></span> <span data-ttu-id="9c45b-122">問題が修正されない場合、通常はデータベースまたはサーバー インスタンスを再起動することで問題が解決されます。</span><span class="sxs-lookup"><span data-stu-id="9c45b-122">If the problem persists, restarting the database or server instance typically corrects the problem.</span></span> <span data-ttu-id="9c45b-123">詳細については、各パートナーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログを参照し、このメッセージに先行する関連エラーがないかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9c45b-123">For more information, look in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log on each partner for the associated error that preceded this message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c45b-124">参照</span><span class="sxs-lookup"><span data-stu-id="9c45b-124">See Also</span></span>  
 [<span data-ttu-id="9c45b-125">データベース ミラーリングの監視 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9c45b-125">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
