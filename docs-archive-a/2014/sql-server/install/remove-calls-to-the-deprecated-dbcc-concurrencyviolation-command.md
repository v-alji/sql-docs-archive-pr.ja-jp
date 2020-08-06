---
title: 非推奨の DBCC CONCURRENCYVIOLATION コマンドの呼び出しを削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cde04ebfc2ea9996d1c9ed233123e5b66f6e81fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737543"
---
# <a name="remove-calls-to-the-deprecated-dbcc-concurrencyviolation-command"></a><span data-ttu-id="9b5f6-102">非推奨の DBCC CONCURRENCYVIOLATION コマンド呼び出しの削除</span><span class="sxs-lookup"><span data-stu-id="9b5f6-102">Remove calls to the deprecated DBCC CONCURRENCYVIOLATION command</span></span>
  <span data-ttu-id="9b5f6-103">アップグレード アドバイザーによって、DBCC CONCURRENCYVIOLATION コマンドの使用が検出されました。</span><span class="sxs-lookup"><span data-stu-id="9b5f6-103">Upgrade Advisor detected the use of the DBCC CONCURRENCYVIOLATION command.</span></span> <span data-ttu-id="9b5f6-104">このコマンドは使用できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="9b5f6-104">This command is no longer available.</span></span> <span data-ttu-id="9b5f6-105">このコマンドを実行すると、エラー 2526 が返されます。</span><span class="sxs-lookup"><span data-stu-id="9b5f6-105">Executing this command returns error 2526.</span></span>  
  
## <a name="component"></a><span data-ttu-id="9b5f6-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="9b5f6-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="9b5f6-107">説明</span><span class="sxs-lookup"><span data-stu-id="9b5f6-107">Description</span></span>  
 <span data-ttu-id="9b5f6-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエディションの新しいバージョンにはワークロード ガバナーが含まれていないため、コマンドは削除されました。</span><span class="sxs-lookup"><span data-stu-id="9b5f6-108">No recent version of edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] includes a workload governor; therefore the command has been removed.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="9b5f6-109">修正措置</span><span class="sxs-lookup"><span data-stu-id="9b5f6-109">Corrective Action</span></span>  
 <span data-ttu-id="9b5f6-110">この非推奨コマンドへの参照を削除するために、アプリケーションおよびスクリプトを更新します。</span><span class="sxs-lookup"><span data-stu-id="9b5f6-110">Update applications and scripts to remove references to this deprecated command.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="9b5f6-111">外部リソース</span><span class="sxs-lookup"><span data-stu-id="9b5f6-111">External Resources</span></span>  
  
