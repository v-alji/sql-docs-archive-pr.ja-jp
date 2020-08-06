---
title: SQL Server Browser のプロパティ ([詳細設定] タブ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ba79137a-cb72-4bf3-a650-e11d02cfce10
author: stevestein
ms.author: sstein
ms.openlocfilehash: 480cd93c3feca44dd455a1a9ce2fd12994ca6100
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644252"
---
# <a name="sql-server-browser-properties-advanced-tab"></a><span data-ttu-id="42e3b-102">[SQL Server Browser のプロパティ] ダイアログ ボックス ([詳細設定] タブ)</span><span class="sxs-lookup"><span data-stu-id="42e3b-102">SQL Server Browser Properties (Advanced Tab)</span></span>
  <span data-ttu-id="42e3b-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser プログラムはサーバー上のサービスとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="42e3b-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser program runs as a service on the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="42e3b-104">Browser では、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各種リソースに関する着信要求を受信し、このコンピューター上にインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="42e3b-104">Browser listens for incoming requests for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="42e3b-105">オプション</span><span class="sxs-lookup"><span data-stu-id="42e3b-105">Options</span></span>  
 <span data-ttu-id="42e3b-106">**クラスター化インデックス**</span><span class="sxs-lookup"><span data-stu-id="42e3b-106">**Clustered**</span></span>  
 <span data-ttu-id="42e3b-107">このサービスがクラスター サーバーのリソースとしてインストールされているかどうかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="42e3b-107">Indicates if this service is installed as a resource of a clustered server.</span></span>  
  
 <span data-ttu-id="42e3b-108">**[カスタマー フィードバック レポート]**</span><span class="sxs-lookup"><span data-stu-id="42e3b-108">**Customer Feedback Reporting**</span></span>  
 <span data-ttu-id="42e3b-109">サービス品質の監視がこのサービスで有効になっているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="42e3b-109">Indicates whether Service Quality Monitoring has been enabled on this service.</span></span> <span data-ttu-id="42e3b-110">カスタマー フィードバック報告の詳細については、オンライン ブックの「エラー レポートと使用状況レポートの設定」を検索してください。</span><span class="sxs-lookup"><span data-stu-id="42e3b-110">For more information on Customer Feedback Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span>  
  
 <span data-ttu-id="42e3b-111">**[ダンプ ディレクトリ]**</span><span class="sxs-lookup"><span data-stu-id="42e3b-111">**Dump Directory**</span></span>  
 <span data-ttu-id="42e3b-112">エラー発生時にメモリ ダンプが配置される場所です。</span><span class="sxs-lookup"><span data-stu-id="42e3b-112">The location where memory dumps are placed in case of an error.</span></span>  
  
 <span data-ttu-id="42e3b-113">**[エラー報告]**</span><span class="sxs-lookup"><span data-stu-id="42e3b-113">**Error Reporting**</span></span>  
 <span data-ttu-id="42e3b-114">**[はい]** に設定した場合、重大な障害が発生したときに、ワトソン博士プログラムによって [!INCLUDE[msCoName](../../includes/msconame-md.md)] またはエラー サーバーに情報が転送されます。</span><span class="sxs-lookup"><span data-stu-id="42e3b-114">When set to **Yes**, the Dr. Watson program forwards information to either [!INCLUDE[msCoName](../../includes/msconame-md.md)] or your error server if a serious failure occurs.</span></span> <span data-ttu-id="42e3b-115">エラー報告の詳細については、オンライン ブックの「エラー レポートと使用状況レポートの設定」を検索してください。</span><span class="sxs-lookup"><span data-stu-id="42e3b-115">For more information on Error Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span>  
  
 <span data-ttu-id="42e3b-116">**インスタンス ID**</span><span class="sxs-lookup"><span data-stu-id="42e3b-116">**Instance ID**</span></span>  
 <span data-ttu-id="42e3b-117">この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント インスタンスを使用した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="42e3b-117">Indicates the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that used this [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent instance.</span></span> <span data-ttu-id="42e3b-118">既定のインスタンスは **MSSQL10_50.MSSQLSERVER**です。</span><span class="sxs-lookup"><span data-stu-id="42e3b-118">The default instance is **MSSQL10_50.MSSQLSERVER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e3b-119">参照</span><span class="sxs-lookup"><span data-stu-id="42e3b-119">See Also</span></span>  
 [<span data-ttu-id="42e3b-120">SQL Server Browser サービス</span><span class="sxs-lookup"><span data-stu-id="42e3b-120">SQL Server Browser Service</span></span>](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
