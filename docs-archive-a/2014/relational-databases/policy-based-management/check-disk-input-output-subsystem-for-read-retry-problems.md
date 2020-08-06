---
title: ディスク入力出力サブシステムに読み取り再試行の問題がないか確認します。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19809b1554e435600eb4eeae424bed17dc27bdbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711906"
---
# <a name="check-disk-input-output-subsystem-for-read-retry-problems"></a><span data-ttu-id="c36fa-102">ディスク I/O サブシステムの読み取り再試行の問題の確認</span><span class="sxs-lookup"><span data-stu-id="c36fa-102">Check Disk Input Output Subsystem for Read Retry Problems</span></span>
  <span data-ttu-id="c36fa-103">このルールでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のイベント ログにエラー メッセージ 825 があるどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="c36fa-103">This rule checks the event log for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error message 825.</span></span> <span data-ttu-id="c36fa-104">このメッセージは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が最初の試行ではディスクからデータを読み取れなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="c36fa-104">This message indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] was unable to read data from the disk on the first try.</span></span> <span data-ttu-id="c36fa-105">このメッセージは、ディスク I/O サブシステムに大きな問題があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="c36fa-105">This message indicates a major problem with the disk I/O subsystem.</span></span> <span data-ttu-id="c36fa-106">このメッセージは、現時点では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の問題を示していませんが、</span><span class="sxs-lookup"><span data-stu-id="c36fa-106">This message does not currently indicate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] problem.</span></span> <span data-ttu-id="c36fa-107">ディスクの問題を解決しないと、データの損失やデータベースの破損につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c36fa-107">However, the disk problem could cause data loss or database corruption if it is not resolved.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="c36fa-108">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="c36fa-108">Best Practices Recommendations</span></span>  
 <span data-ttu-id="c36fa-109">次の操作を行って、原因となっているハードウェアの問題を特定し、解決してください。</span><span class="sxs-lookup"><span data-stu-id="c36fa-109">The following actions might help you discover and resolve the underlying hardware problem:</span></span>  
  
-   <span data-ttu-id="c36fa-110">このメッセージのエラー ログと変数テキストを確認し、問題の原因を明らかにする手掛かりを見つける。</span><span class="sxs-lookup"><span data-stu-id="c36fa-110">Review the error log and the variable text in this message for clues that explain the problem.</span></span>  
  
-   <span data-ttu-id="c36fa-111">ディスク システムを確認する。</span><span class="sxs-lookup"><span data-stu-id="c36fa-111">Check the disk system.</span></span> <span data-ttu-id="c36fa-112">この問題は、ディスク、ディスク コントローラー、アレイ カード、またはディスク ドライバーに関連している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c36fa-112">The problem could be related to the disks, the disk controllers, array cards, or disk drivers.</span></span>  
  
-   <span data-ttu-id="c36fa-113">ディスク システムの状態を調べる最新のユーティリティがあるかどうか、ディスクの製造元に問い合わせる。</span><span class="sxs-lookup"><span data-stu-id="c36fa-113">Contact the disk manufacturer for the latest utilities for checking the status of the disk system.</span></span>  
  
-   <span data-ttu-id="c36fa-114">ドライバーの最新の更新があるかどうか、ディスクの製造元に問い合わせる。</span><span class="sxs-lookup"><span data-stu-id="c36fa-114">Contact the disk manufacturer for the latest driver updates.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="c36fa-115">詳細情報</span><span class="sxs-lookup"><span data-stu-id="c36fa-115">For More Information</span></span>  
 [<span data-ttu-id="c36fa-116">MSSQLSERVER_825</span><span class="sxs-lookup"><span data-stu-id="c36fa-116">MSSQLSERVER_825</span></span>](../errors-events/mssqlserver-825-database-engine-error.md)  
  
 <span data-ttu-id="c36fa-117">[SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="c36fa-117">[SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span></span>  
  
  
