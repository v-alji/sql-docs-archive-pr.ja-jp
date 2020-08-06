---
title: SQL Server ユーティリティへの接続 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b9b90b8d-241f-4b74-ac14-de7b10ea1821
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e8e59a28e083fc302faebbcba932c18a04e73a7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633144"
---
# <a name="connect-to-a-sql-server-utility"></a><span data-ttu-id="3f0b2-102">SQL Server ユーティリティへの接続</span><span class="sxs-lookup"><span data-stu-id="3f0b2-102">Connect to a SQL Server Utility</span></span>
  <span data-ttu-id="3f0b2-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに接続する前に、ユーティリティ コントロール ポイント (UCP) を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-103">Before you can connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, you must create a utility control point (UCP).</span></span> <span data-ttu-id="3f0b2-104">詳細については、「 [SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-104">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>

 <span data-ttu-id="3f0b2-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のリソース正常性を表示および管理するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに接続します。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-105">To view and manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource health, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>

 <span data-ttu-id="3f0b2-106">SSMS を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに接続するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-106">To connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility through SSMS:</span></span>

1.  <span data-ttu-id="3f0b2-107">SSMS を起動します。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-107">Launch SSMS.</span></span>

2.  <span data-ttu-id="3f0b2-108">SSMS で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-108">In SSMS, connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>

3.  <span data-ttu-id="3f0b2-109">**[表示]** をクリックし、 **[ユーティリティ エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-109">Click **View** and then **Utility Explorer**.</span></span>

4.  <span data-ttu-id="3f0b2-110">ユーティリティ エクスプローラーのナビゲーション ウィンドウで、![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility") **[ユーティリティへの接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-110">In the Utility Explorer navigation pane, click ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")**Connect to Utility**.</span></span>

5.  <span data-ttu-id="3f0b2-111">**[サーバーへの接続]** ダイアログ ボックスで、UCP インスタンス名を指定し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-111">In the **Connect to Server** dialog box, specify the UCP instance name, then click **Connect**.</span></span>

6.  <span data-ttu-id="3f0b2-112">ユーティリティ エクスプローラーのナビゲーション ウィンドウを表示し、UCP の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースのツリー ビューを表示します。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-112">View the Utility Explorer Navigation Pane to see a tree view of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources in the UCP.</span></span>

 <span data-ttu-id="3f0b2-113">新しい UCP を作成した場合も、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに接続されます。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-113">Creating a new UCP also connects you to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="3f0b2-114">詳細については、「[SQL Server ユーティリティ コントロール ポイントの作成 &#40;SQL Server ユーティリティ&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-114">For more information, see [Create a SQL Server Utility Control Point &#40;SQL Server Utility&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3f0b2-115">参照</span><span class="sxs-lookup"><span data-stu-id="3f0b2-115">See Also</span></span>
 <span data-ttu-id="3f0b2-116">[SQL Server ユーティリティの機能とタスクの](sql-server-utility-features-and-tasks.md)[表示 Resource Health ポリシーの結果を表示 &#40;SQL Server ユーティリティ&#41;](view-resource-health-policy-results-sql-server-utility.md)</span><span class="sxs-lookup"><span data-stu-id="3f0b2-116">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) [View Resource Health Policy Results &#40;SQL Server Utility&#41;](view-resource-health-policy-results-sql-server-utility.md)</span></span>


