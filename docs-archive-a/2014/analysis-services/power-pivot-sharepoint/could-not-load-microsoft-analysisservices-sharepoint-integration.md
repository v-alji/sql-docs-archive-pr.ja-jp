---
title: ファイルまたはアセンブリ &#39;読み込むことができませんでした。サービス、バージョン = 3.5.0.0、Culture = ニュートラル、PublicKeyToken = b77a5c561934e089&#39;、またはその依存関係の1つです。 指定されたファイルが見つかりません。 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f9eed7ad90c1e720d07c714e351c24ae6657717
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643547"
---
# <a name="could-not-load-file-or-assembly-39microsoftdataservices-version3500-cultureneutral-publickeytokenb77a5c561934e08939-or-one-of-its-dependencies-the-system-cannot-find-the-file-specified"></a><span data-ttu-id="36936-104">ファイルまたはアセンブリ &#39;読み込むことができませんでした。サービス、バージョン = 3.5.0.0、Culture = ニュートラル、PublicKeyToken = b77a5c561934e089&#39;、またはその依存関係の1つです。</span><span class="sxs-lookup"><span data-stu-id="36936-104">Could not load file or assembly &#39;Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089&#39; or one of its dependencies.</span></span> <span data-ttu-id="36936-105">指定されたファイルが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="36936-105">The system cannot find the file specified.</span></span>
  <span data-ttu-id="36936-106">PowerPivot for SharePoint がある SharePoint 2010 環境では、データ フィードのエクスポートを実行しようとした場合に必要なバージョンの Microsoft ADO.NET Data Services がないと、このエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="36936-106">In SharePoint 2010 environments that have PowerPivot for SharePoint, this error will occur if you attempt a data feed export and the system is missing the required version of Microsoft ADO.NET Data Services.</span></span>  
  
## <a name="details"></a><span data-ttu-id="36936-107">詳細</span><span class="sxs-lookup"><span data-stu-id="36936-107">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="36936-108">適用対象</span><span class="sxs-lookup"><span data-stu-id="36936-108">Applies to</span></span>|<span data-ttu-id="36936-109">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="36936-109">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="36936-110">製品バージョン</span><span class="sxs-lookup"><span data-stu-id="36936-110">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="36936-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36936-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="36936-112">原因</span><span class="sxs-lookup"><span data-stu-id="36936-112">Cause</span></span>|<span data-ttu-id="36936-113">ADO.NET Data Services 3.5 SP1 が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="36936-113">ADO.NET Data Services 3.5 SP1 was not found.</span></span>|  
|<span data-ttu-id="36936-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="36936-114">Message Text</span></span>|<span data-ttu-id="36936-115">ファイルまたはアセンブリ 'Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'、またはその依存関係の 1 つが読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="36936-115">Could not load file or assembly 'Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.</span></span> <span data-ttu-id="36936-116">指定されたファイルが見つかりません</span><span class="sxs-lookup"><span data-stu-id="36936-116">The system cannot find the file specified</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="36936-117">説明</span><span class="sxs-lookup"><span data-stu-id="36936-117">Explanation</span></span>  
 <span data-ttu-id="36936-118">SharePoint 2010 には、SharePoint リストを XML データ フィードとしてエクスポートするための [データ フィードとしてエクスポート] ボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="36936-118">SharePoint 2010 includes an Export as Data Feed button that you can use to export a SharePoint list as an XML data feed.</span></span> <span data-ttu-id="36936-119">また、SharePoint モードの Reporting Services と PowerPivot for SharePoint では、ADO.NET Data Services を必要とするデータ フィード機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="36936-119">In addition, both Reporting Services in SharePoint mode and PowerPivot for SharePoint support data feed features that require ADO.NET Data Services.</span></span>  
  
 <span data-ttu-id="36936-120">ADO.NET Data Services がインストールされていない場合、データ フィードを実行しようとすると、このエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="36936-120">If ADO.NET Data Services is not installed, this error will occur when you request a data feed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="36936-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="36936-121">User Action</span></span>  
  
1.  <span data-ttu-id="36936-122">SharePoint 2010 のハードウェアとソフトウェアの要件に関するドキュメントにアクセスし、[ハードウェアとソフトウェアの要件を決定します (sharepoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734) (「」を参照して https://go.microsoft.com/fwlink/?LinkId=169734) ください。</span><span class="sxs-lookup"><span data-stu-id="36936-122">Go to the hardware and software requirements documentation for SharePoint 2010, [Determine Hardware and Software Requirements (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734) (https://go.microsoft.com/fwlink/?LinkId=169734).</span></span>  
  
2.  <span data-ttu-id="36936-123">「**必要なソフトウェアのインストール**」で、使用しているオペレーティングシステムに対応する ADO.NET Data Services 3.5 のリンクを見つけます。</span><span class="sxs-lookup"><span data-stu-id="36936-123">In **Installing software prerequisites**, find the link for ADO.NET Data Services 3.5 that corresponds to the operating system you are using.</span></span>  
  
3.  <span data-ttu-id="36936-124">リンクをクリックし、サービスをインストールするセットアップ プログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="36936-124">Click the link and run the setup program that installs the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36936-125">参照</span><span class="sxs-lookup"><span data-stu-id="36936-125">See Also</span></span>  
 [<span data-ttu-id="36936-126">SharePoint への PowerPivot ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="36936-126">Deploy PowerPivot Solutions to SharePoint</span></span>](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
