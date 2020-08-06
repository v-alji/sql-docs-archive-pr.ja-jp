---
title: 'ブックのデータ接続パスがローカル ドライブ上のファイルを指しているか、無効な URI です。 次の接続を更新できませんでした: PowerPivot Data |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: bd22e41a-0931-4d32-888a-633a3046fc5e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3349af08290e2ff659db1441d849b2afef51e95b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640272"
---
# <a name="the-data-connection-path-in-the-workbook-points-to-a-file-on-the-local-drive-or-is-an-invalid-uri-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="3acf0-103">ブックのデータ接続パスがローカル ドライブ上のファイルを指しているか、無効な URI です。</span><span class="sxs-lookup"><span data-stu-id="3acf0-103">The data connection path in the workbook points to a file on the local drive or is an invalid URI.</span></span> <span data-ttu-id="3acf0-104">次の接続の更新に失敗しました:PowerPivot データ</span><span class="sxs-lookup"><span data-stu-id="3acf0-104">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="3acf0-105">PowerPivot データを含む Excel ブックで、Excel Services は、埋め込みデータ ソースに接続できない場合にこのエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="3acf0-105">For Excel workbooks that contain PowerPivot data, Excel Services returns this error if it cannot connect to embedded data sources.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3acf0-106">詳細</span><span class="sxs-lookup"><span data-stu-id="3acf0-106">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3acf0-107">適用対象</span><span class="sxs-lookup"><span data-stu-id="3acf0-107">Applies to</span></span>|<span data-ttu-id="3acf0-108">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="3acf0-108">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="3acf0-109">製品バージョン</span><span class="sxs-lookup"><span data-stu-id="3acf0-109">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="3acf0-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3acf0-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="3acf0-111">原因</span><span class="sxs-lookup"><span data-stu-id="3acf0-111">Cause</span></span>|<span data-ttu-id="3acf0-112">信頼できるデータ接続ライブラリにある .odc ファイルからのデータ接続のみ許可するように Excel Services が構成されています。</span><span class="sxs-lookup"><span data-stu-id="3acf0-112">Excel Services is configured to only allow data connections from .odc files that are in a trusted data connection library.</span></span>|  
|<span data-ttu-id="3acf0-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="3acf0-113">Message Text</span></span>|<span data-ttu-id="3acf0-114">ブックのデータ接続パスがローカル ドライブ上のファイルを指しているか、無効な URI です。</span><span class="sxs-lookup"><span data-stu-id="3acf0-114">The data connection path in the workbook points to a file on the local drive or is an invalid URI.</span></span> <span data-ttu-id="3acf0-115">次の接続の更新に失敗しました:PowerPivot データ</span><span class="sxs-lookup"><span data-stu-id="3acf0-115">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3acf0-116">説明</span><span class="sxs-lookup"><span data-stu-id="3acf0-116">Explanation</span></span>  
 <span data-ttu-id="3acf0-117">PowerPivot ブックには、埋め込みデータ接続が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3acf0-117">PowerPivot workbooks contain embedded data connections.</span></span> <span data-ttu-id="3acf0-118">スライサーやフィルターを介したブックの操作をサポートするには、埋め込まれている接続情報を使用した外部データ アクセスを許可するように Excel Services を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3acf0-118">To support workbook interaction through slicers and filters, Excel Services must be configured to allow external data access through embedded connection information.</span></span> <span data-ttu-id="3acf0-119">外部データ アクセスは、ファームの PowerPivot サーバーに読み込まれる PowerPivot データを取得するのに必要です。</span><span class="sxs-lookup"><span data-stu-id="3acf0-119">External data access is required for retrieving PowerPivot data that is loaded on PowerPivot servers in the farm.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3acf0-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="3acf0-120">User Action</span></span>  
 <span data-ttu-id="3acf0-121">埋め込みデータ ソース接続を許可するように構成設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="3acf0-121">Change the configuration settings to allow embedded data source connections.</span></span>  
  
1.  <span data-ttu-id="3acf0-122">サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3acf0-122">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="3acf0-123">**[Excel Services アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3acf0-123">Click **Excel Services Application**.</span></span>  
  
3.  <span data-ttu-id="3acf0-124">**[信頼できるファイル保存場所]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3acf0-124">Click **Trusted File Location**.</span></span>  
  
4.  <span data-ttu-id="3acf0-125">**[http://]** または構成する場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3acf0-125">Click **http://** or the location you want to configure.</span></span>  
  
5.  <span data-ttu-id="3acf0-126">[外部データ] の [外部データの許可] で、 **[信頼できるデータ接続ライブラリと、埋め込まれている接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3acf0-126">In External Data, in Allow External Data, click **Trusted data connection libraries and embedded**.</span></span>  
  
6.  <span data-ttu-id="3acf0-127">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3acf0-127">Click **OK**.</span></span>  
  
 <span data-ttu-id="3acf0-128">または、PowerPivot ブックが含まれるサイト用に新しく信頼できる場所を作成し、そのサイトの構成設定だけを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="3acf0-128">Alternatively, you can create a new trusted location for sites that contain PowerPivot workbooks, and then modify the configuration settings for just that site.</span></span> <span data-ttu-id="3acf0-129">詳細については、「 [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3acf0-129">For more information, see [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).</span></span>  
  
  
