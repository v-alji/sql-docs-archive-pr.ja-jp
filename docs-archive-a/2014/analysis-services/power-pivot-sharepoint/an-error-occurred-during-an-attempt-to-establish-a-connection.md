---
title: '外部データ ソースへの接続を確立しようとしましたが、エラーが発生しました。 次の接続を更新できませんでした: PowerPivot Data |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1b951da1-f62d-43d2-b40b-270a4a9ab92c
author: minewiskan
ms.author: owend
ms.openlocfilehash: eb4329440b69d1bdfdbb96fbcc3926fa000d8877
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715769"
---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection-to-the-external-data-source-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="475e7-103">外部データ ソースへの接続を確立しようとしましたが、エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="475e7-103">An error occurred during an attempt to establish a connection to the external data source.</span></span> <span data-ttu-id="475e7-104">次の接続の更新に失敗しました:PowerPivot データ</span><span class="sxs-lookup"><span data-stu-id="475e7-104">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="475e7-105">このエラーは、PowerPivot for SharePoint がインストールされていないサーバーで PowerPivot データのクエリを実行した場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="475e7-105">This error occurs if you query PowerPivot data on a server that does not have PowerPivot for SharePoint installed.</span></span> <span data-ttu-id="475e7-106">また、SQL Server Analysis Services (PowerPivot) サービスが停止した場合や、PowerPivot データを以前のバージョンで表示しようとした場合にも発生します。</span><span class="sxs-lookup"><span data-stu-id="475e7-106">It also occurs if the SQL Server Analysis Services (PowerPivot) service is stopped, or if you are attempting to view PowerPivot data from an earlier version.</span></span>  
  
## <a name="details"></a><span data-ttu-id="475e7-107">詳細</span><span class="sxs-lookup"><span data-stu-id="475e7-107">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="475e7-108">適用対象</span><span class="sxs-lookup"><span data-stu-id="475e7-108">Applies to</span></span>|<span data-ttu-id="475e7-109">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="475e7-109">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="475e7-110">製品バージョン</span><span class="sxs-lookup"><span data-stu-id="475e7-110">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="475e7-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="475e7-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="475e7-112">原因</span><span class="sxs-lookup"><span data-stu-id="475e7-112">Cause</span></span>|<span data-ttu-id="475e7-113">データ接続に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="475e7-113">The data connection failed.</span></span>|  
|<span data-ttu-id="475e7-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="475e7-114">Message Text</span></span>|<span data-ttu-id="475e7-115">外部データ ソースへの接続を確立しようとしましたが、エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="475e7-115">An error occurred during an attempt to establish a connection to the external data source.</span></span> <span data-ttu-id="475e7-116">次の接続の更新に失敗しました:PowerPivot データ</span><span class="sxs-lookup"><span data-stu-id="475e7-116">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="475e7-117">説明</span><span class="sxs-lookup"><span data-stu-id="475e7-117">Explanation</span></span>  
 <span data-ttu-id="475e7-118">SharePoint にパブリッシュされた Excel ブック内の PowerPivot データのクエリを実行するときに SharePoint 環境に PowerPivot for SharePoint サーバーがないか、SQL Server Analysis Services (PowerPivot) サービスが停止している場合は、Excel Services からこのエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="475e7-118">Excel Services returns this error when you query PowerPivot data in an Excel workbook that is published to SharePoint, and the SharePoint environment does not have a PowerPivot for SharePoint server, or the SQL Server Analysis Services (PowerPivot) service is stopped.</span></span>  
  
 <span data-ttu-id="475e7-119">このエラーは、クエリ エンジンを使用できないときに PowerPivot データのスライスまたはフィルター処理を行うと発生します。</span><span class="sxs-lookup"><span data-stu-id="475e7-119">The error occurs when you slice or filter PowerPivot data when the query engine is not available.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="475e7-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="475e7-120">User Action</span></span>  
 <span data-ttu-id="475e7-121">PowerPivot for SharePoint をインストールするか、PowerPivot for SharePoint がインストールされた SharePoint 環境に PowerPivot ブックを移動します。</span><span class="sxs-lookup"><span data-stu-id="475e7-121">Install PowerPivot for SharePoint or move the PowerPivot workbook to a SharePoint environment that has PowerPivot for SharePoint installed.</span></span> <span data-ttu-id="475e7-122">詳しくは、「 [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="475e7-122">For more information, see [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md).</span></span>  
  
 <span data-ttu-id="475e7-123">このソフトウェアがインストールされている場合は、SQL Server Analysis Services (PowerPivot) のインスタンスが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="475e7-123">If the software is installed, verify that the SQL Server Analysis Services (PowerPivot) instance is running.</span></span> <span data-ttu-id="475e7-124">サーバーの全体管理で、 **[サーバーのサービスの管理]** を確認します。</span><span class="sxs-lookup"><span data-stu-id="475e7-124">Check **Manage services on server** in Central Administration.</span></span> <span data-ttu-id="475e7-125">また、管理ツールの [サービス] コンソール アプリケーションも確認します。</span><span class="sxs-lookup"><span data-stu-id="475e7-125">Also check the Services console application in Administrative Tools.</span></span>  
  
 <span data-ttu-id="475e7-126">SQL Server 2008 R2 バージョンの PowerPivot for Excel で作成された PowerPivot ブックの場合、SQL Server 2008 R2 バージョンの Analysis Services OLE DB プロバイダーをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="475e7-126">For PowerPivot workbooks that were created in a SQL Server 2008 R2 version of PowerPivot for Excel, you must install the SQL Server 2008 R2 version of the Analysis Services OLE DB provider.</span></span> <span data-ttu-id="475e7-127">プロバイダーをインストールし、Microsoft.AnalysisServices.ChannelTransport.dll ファイルを登録しなかった場合、このエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="475e7-127">This error will occur if you installed the provider, but did not register the Microsoft.AnalysisServices.ChannelTransport.dll file.</span></span> <span data-ttu-id="475e7-128">ファイルの登録の詳細については、「 [SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="475e7-128">For more information about file registration, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="475e7-129">参照</span><span class="sxs-lookup"><span data-stu-id="475e7-129">See Also</span></span>  
 [<span data-ttu-id="475e7-130">データ接続は Windows 認証を使用しており、ユーザーの資格情報を委任できませんでした。次の接続を更新できませんでした: PowerPivot データ</span><span class="sxs-lookup"><span data-stu-id="475e7-130">The data connection uses Windows Authentication and user credentials could not be delegated. The following connections failed to refresh: PowerPivot Data</span></span>](the-data-connection-user-could-not-be-delegated.md)  
  
  
