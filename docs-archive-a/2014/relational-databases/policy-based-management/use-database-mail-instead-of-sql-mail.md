---
title: SQL Mail ではなくデータベース メールを使用する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a6a957b65975645bdeb9f55faee4e650b53718b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634444"
---
# <a name="use-database-mail-instead-of-sql-mail"></a><span data-ttu-id="30524-102">SQL Mail ではなくデータベース メールを使用する</span><span class="sxs-lookup"><span data-stu-id="30524-102">Use Database Mail Instead of SQL Mail</span></span>
  <span data-ttu-id="30524-103">このルールでは、sys.configurations カタログ ビューを確認して、サーバー全体に適用される構成オプションである SQL Mail XPs が ON に設定されているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="30524-103">This rule checks the sys.configurations catalog view to determine whether the SQL Mail XPs server-wide configuration option is set to ON.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="30524-104">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="30524-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="30524-105">SQL Mail は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の将来のバージョンで削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="30524-105">SQL Mail will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="30524-106">新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="30524-106">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span> <span data-ttu-id="30524-107">メールを送信するには、データベース メールを使用してください。</span><span class="sxs-lookup"><span data-stu-id="30524-107">To send mail, use Database Mail.</span></span>  
  
 <span data-ttu-id="30524-108">SQL Mail は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスに対してインプロセスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="30524-108">SQL Mail runs in-process to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="30524-109">SQL Mail がダウンした場合、サーバーもダウンします。</span><span class="sxs-lookup"><span data-stu-id="30524-109">If SQL Mail goes down, so does the server.</span></span> <span data-ttu-id="30524-110">データベース メールは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 外部の別個のプロセスで実行され、スケーラブルです。拡張 MAPI クライアント コンポーネントを実稼働サーバーにインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="30524-110">Database Mail runs outside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a separate process, is scalable, and does not require Extended MAPI client components to be installed on the production server.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="30524-111">詳細情報</span><span class="sxs-lookup"><span data-stu-id="30524-111">For More Information</span></span>  
 [<span data-ttu-id="30524-112">データベース メール</span><span class="sxs-lookup"><span data-stu-id="30524-112">Database Mail</span></span>](../database-mail/database-mail.md)  
  
## <a name="see-also"></a><span data-ttu-id="30524-113">参照</span><span class="sxs-lookup"><span data-stu-id="30524-113">See Also</span></span>  
 [<span data-ttu-id="30524-114">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="30524-114">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
