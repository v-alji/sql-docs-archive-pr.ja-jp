---
title: Excel Services の信頼された Data Provider として MSOLAP を追加する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c1f40fa4-de6d-41ee-8124-14b4d65988f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 876ec613f18b2d91b5e06ab5fed4a7b258c30a36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644179"
---
# <a name="add-msolap5-as-a-trusted-data-provider-in-excel-services"></a><span data-ttu-id="5eea1-102">Excel Services で信頼できるデータ プロバイダーとして MSOLAP.5 を追加</span><span class="sxs-lookup"><span data-stu-id="5eea1-102">Add MSOLAP.5 as a Trusted Data Provider in Excel Services</span></span>
  <span data-ttu-id="5eea1-103">MSOLAP.5 は、SQL Server 2012 用の Analysis Services OLE DB プロバイダーです。</span><span class="sxs-lookup"><span data-stu-id="5eea1-103">MSOLAP.5 refers to the Analysis Services OLE DB provider for SQL Server 2012.</span></span> <span data-ttu-id="5eea1-104">Excel Services は、サーバー上の PowerPivot データを利用可能とする接続要求を行う前に、このプロバイダーを信頼する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5eea1-104">Excel Services must trust this provider before it will make the connection request that results in the availability of PowerPivot data on a server.</span></span>  
  
 <span data-ttu-id="5eea1-105">PowerPivot 構成ツールを使用して PowerPivot for SharePoint を構成した場合、このツールは要件を満たすアクションを含むため、MSOLAP.5 は、既に信頼されたプロバイダーとなっている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5eea1-105">If you configured PowerPivot for SharePoint using the PowerPivot Configuration Tool, MSOLAP.5 might already be a trusted provider because the tool includes an action that satisfies this requirement.</span></span> <span data-ttu-id="5eea1-106">ただし、PowerShell や全体管理を使用している場合、または信頼されたプロバイダー アクションを構成ツールで除外している場合は、このプロバイダーが不足している可能性があります。その場合は、PowerPivot データ アクセスのファームを構成するときに、それを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5eea1-106">However, if you are using PowerShell, Central Administration, or if you excluded the trusted provider action in the configuration tool, the provider might be missing, which case you should add it now as part of configuring the farm for PowerPivot data access.</span></span>  
  
 <span data-ttu-id="5eea1-107">この手順は、各 Excel Services サービス アプリケーションにつき 1 回実行するだけです。</span><span class="sxs-lookup"><span data-stu-id="5eea1-107">You only need to perform this step once for each Excel Services service application.</span></span>  
  
 <span data-ttu-id="5eea1-108">PowerPivot for SharePoint サーバーまたは Excel Services サーバーなど、PowerPivot データ要求を処理する物理サーバーでは、コンピューターに OLE DB プロバイダーをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5eea1-108">Each physical server that handles a PowerPivot data request, such as a PowerPivot for SharePoint server or an Excel Services server, must have the OLE DB provider installed on the computer.</span></span> <span data-ttu-id="5eea1-109">PowerPivot for SharePoint のインストールには常に OLE DB プロバイダーが含まれていますが、PowerPivot for SharePoint がないコンピューターで Excel Services が実行されている場合は、プロバイダーを手動でインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5eea1-109">A PowerPivot for SharePoint installation always includes the OLE DB provider, but if Excel Services is running on a computer that does not have PowerPivot for SharePoint, you must install the provider manually.</span></span> <span data-ttu-id="5eea1-110">「 [SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eea1-110">For more information, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).</span></span>  
  
## <a name="add-a-trusted-provider-to-excel-services"></a><span data-ttu-id="5eea1-111">Excel Services に信頼できるプロバイダーを追加する</span><span class="sxs-lookup"><span data-stu-id="5eea1-111">Add a trusted provider to Excel Services</span></span>  
  
1.  <span data-ttu-id="5eea1-112">サーバーの全体管理で、 **[アプリケーション構成の管理]** をクリックし、Excel Services サービス アプリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5eea1-112">In Central Administration, click **Manage service applications**, and then click the Excel Services service application.</span></span>  
  
2.  <span data-ttu-id="5eea1-113">**[信頼できるデータ プロバイダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5eea1-113">Click **Trusted Data Providers**.</span></span>  
  
3.  <span data-ttu-id="5eea1-114">MSOLAP.5 が一覧に表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5eea1-114">Verify that MSOLAP.5 appears in the list.</span></span> <span data-ttu-id="5eea1-115">PowerPivot for SharePoint の構成方法によっては、MSOLAP.5 が既に信頼されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="5eea1-115">Depending on how you configured PowerPivot for SharePoint, MSOLAP.5 might already be trusted.</span></span>  
  
4.  <span data-ttu-id="5eea1-116">表示されない場合は、 **[信頼できるデータ プロバイダーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5eea1-116">If it is not listed, click **Add Trusted Data Provider**.</span></span>  
  
5.  <span data-ttu-id="5eea1-117">[プロバイダー ID] に、「`MSOLAP.5`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="5eea1-117">In Provider ID, type `MSOLAP.5`.</span></span>  
  
6.  <span data-ttu-id="5eea1-118">[プロバイダーの種類] では、OLE DB が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5eea1-118">For Provider Type, ensure that OLE DB is selected.</span></span>  
  
7.  <span data-ttu-id="5eea1-119">[プロバイダーの説明] に、「 **Microsoft OLE DB プロバイダー (OLAP Services 11.0 用)**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="5eea1-119">In Provider Description, type **Microsoft OLE DB Provider for OLAP Services 11.0**.</span></span>  
  
  
