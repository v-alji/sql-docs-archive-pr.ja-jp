---
title: パッケージ実行およびその他の操作の監視 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cbbcd79f-ab9b-46ec-84cb-4821c1d16b99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 628b62d9c8e01d0dc0bf641551de67c3838a4504
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645738"
---
# <a name="monitoring-for-package-executions-and-other-operations"></a><span data-ttu-id="a9f26-102">パッケージの実行およびその他の操作の監視</span><span class="sxs-lookup"><span data-stu-id="a9f26-102">Monitoring for Package Executions and Other Operations</span></span>
  <span data-ttu-id="a9f26-103">次の 1 つ以上のツールを使用して、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行、プロジェクトの検証、およびその他の操作を監視できます。</span><span class="sxs-lookup"><span data-stu-id="a9f26-103">You can monitor [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package executions, project validations, and other operations by using one of more of the following tools.</span></span> <span data-ttu-id="a9f26-104">データ タップなどの特定のツールは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置されたプロジェクトに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a9f26-104">Certain tools such as data taps are available only for projects that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
-   <span data-ttu-id="a9f26-105">ログ</span><span class="sxs-lookup"><span data-stu-id="a9f26-105">Logs</span></span>  
  
     <span data-ttu-id="a9f26-106">詳細については、「[Integration Services (SSIS) のログ記録](integration-services-ssis-logging.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a9f26-106">For more information, see [Integration Services &#40;SSIS&#41; Logging](integration-services-ssis-logging.md).</span></span>  
  
-   <span data-ttu-id="a9f26-107">Reports</span><span class="sxs-lookup"><span data-stu-id="a9f26-107">Reports</span></span>  
  
     <span data-ttu-id="a9f26-108">詳細については、「 [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9f26-108">For more information, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
-   <span data-ttu-id="a9f26-109">ビュー</span><span class="sxs-lookup"><span data-stu-id="a9f26-109">Views</span></span>  
  
     <span data-ttu-id="a9f26-110">詳細については、「[ビュー &#40Integration Services カタログ&#41;](/sql/integration-services/system-views/views-integration-services-catalog)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9f26-110">For more information, see [Views &#40;Integration Services Catalog&#41;](/sql/integration-services/system-views/views-integration-services-catalog).</span></span>  
  
-   <span data-ttu-id="a9f26-111">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="a9f26-111">Performance counters</span></span>  
  
     <span data-ttu-id="a9f26-112">これらのパフォーマンス カウンターの詳細については、「 [パフォーマンス カウンター](performance-counters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9f26-112">For more information, see [Performance Counters](performance-counters.md).</span></span>  
  
-   <span data-ttu-id="a9f26-113">データ タップ</span><span class="sxs-lookup"><span data-stu-id="a9f26-113">Data taps</span></span>  
  
## <a name="operation-types"></a><span data-ttu-id="a9f26-114">操作の種類</span><span class="sxs-lookup"><span data-stu-id="a9f26-114">Operation Types</span></span>  
 <span data-ttu-id="a9f26-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバー上の `SSISDB` カタログでは、さまざまな種類の操作が監視されます。</span><span class="sxs-lookup"><span data-stu-id="a9f26-115">Several different types of operations are monitored in the `SSISDB` catalog, on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="a9f26-116">各操作には、複数のメッセージを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="a9f26-116">Each operation can have multiple messages associated with it.</span></span> <span data-ttu-id="a9f26-117">各メッセージは、複数の種類のうちの 1 つに分類できます。</span><span class="sxs-lookup"><span data-stu-id="a9f26-117">Each message can be classified into one of several different types.</span></span> <span data-ttu-id="a9f26-118">たとえば、メッセージの種類は、情報、警告、またはエラーとなります。</span><span class="sxs-lookup"><span data-stu-id="a9f26-118">For example, a message can be of type Information, Warning, or Error.</span></span> <span data-ttu-id="a9f26-119">メッセージの種類の一覧については、Transact-SQL の [catalog.operation_messages &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database) ビューに関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9f26-119">For the full list of message types, see the documentation for the Transact-SQL [catalog.operation_messages &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database) view.</span></span> <span data-ttu-id="a9f26-120">操作の種類の一覧については、「[catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9f26-120">For a full list of the operations types, see [catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database).</span></span>  
  
 <span data-ttu-id="a9f26-121">9 つの状態の種類を使用して、操作の状態を示します。</span><span class="sxs-lookup"><span data-stu-id="a9f26-121">Nine different status types are used to indicate the status of an operation.</span></span> <span data-ttu-id="a9f26-122">状態の種類の一覧については、「[catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9f26-122">For a full list of the status types, see the [catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database) view.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="a9f26-123">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="a9f26-123">Related Content</span></span>  
 <span data-ttu-id="a9f26-124">blogs.msdn.com のブログ エントリ「 [SSIS の T-SQL API の概要](https://go.microsoft.com/fwlink/?LinkId=249051)」</span><span class="sxs-lookup"><span data-stu-id="a9f26-124">Blog entry, [SSIS T-SQL API Overview](https://go.microsoft.com/fwlink/?LinkId=249051), on blogs.msdn.com.</span></span>  
  
  
