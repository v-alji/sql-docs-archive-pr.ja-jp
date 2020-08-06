---
title: 既定のトレース ログ ファイルの無効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0fed8fb006427b4dda9d99c57cbabca8538efcad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634463"
---
# <a name="default-trace-log-files-disabled"></a><span data-ttu-id="a49e2-102">既定のトレース ログ ファイルの無効化</span><span class="sxs-lookup"><span data-stu-id="a49e2-102">Default Trace Log Files Disabled</span></span>
  <span data-ttu-id="a49e2-103">このルールでは、sp_configure システム ストアド プロシージャの default trace enabled オプションの値を調べて、既定のトレースが ON (1) または OFF (0) のどちらに設定されているかを確認します。</span><span class="sxs-lookup"><span data-stu-id="a49e2-103">This rule checks the value of the sp_configure stored procedure default trace enabled option to determine whether default trace is set ON (1) or OFF (0).</span></span> <span data-ttu-id="a49e2-104">このオプションを有効にした場合、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]に対する構成および DDL の変更に関する情報が既定のトレースによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="a49e2-104">When this option is enabled, default tracing provides information about configuration and DDL changes to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="a49e2-105">この情報は、顧客および [!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービスが、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]に関する問題のトラブルシューティングを行うときに役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="a49e2-105">In some cases, this information can be helpful for customers and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support when they troubleshooting issues with the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="a49e2-106">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="a49e2-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="a49e2-107">sp_configure stored ストアド プロシージャを使用して default trace enabled の値を 1 に設定することで、トレースを有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="a49e2-107">Use the sp_configure stored procedure to enable tracing by setting the value of default trace enabled to 1.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="a49e2-108">詳細情報</span><span class="sxs-lookup"><span data-stu-id="a49e2-108">For More Information</span></span>  
 [<span data-ttu-id="a49e2-109">サーバー構成オプション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a49e2-109">Server Configuration Options &#40;SQL Server&#41;</span></span>](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="a49e2-110">参照</span><span class="sxs-lookup"><span data-stu-id="a49e2-110">See Also</span></span>  
 [<span data-ttu-id="a49e2-111">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="a49e2-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
