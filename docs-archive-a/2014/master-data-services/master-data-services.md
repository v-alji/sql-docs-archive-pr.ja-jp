---
title: マスターデータサービス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 87d8c588c3893a5aadf950a60681ec60d50309de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641717"
---
# <a name="master-data-services"></a><span data-ttu-id="99c70-102">マスター データ サービス</span><span class="sxs-lookup"><span data-stu-id="99c70-102">Master Data Services</span></span>
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] <span data-ttu-id="99c70-103">(MDS) は、マスター データ管理のための [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="99c70-103">(MDS) is the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] solution for master data management.</span></span> <span data-ttu-id="99c70-104">マスター データ管理 (MDM) とは、メンテナンス可能な形でマスターのリストをまとめることを目標に、データの非トランザクション リストを探索および定義するために組織が必要とする作業を表します。</span><span class="sxs-lookup"><span data-stu-id="99c70-104">Master data management (MDM) describes the efforts made by an organization to discover and define non-transactional lists of data, with the goal of compiling maintainable master lists.</span></span> <span data-ttu-id="99c70-105">MDM プロジェクトには、一般に、MDM テクノロジの実装と共に内部ビジネス プロセスの評価および再構築が含まれます。</span><span class="sxs-lookup"><span data-stu-id="99c70-105">An MDM project generally includes an evaluation and restructuring of internal business processes along with the implementation of MDM technology.</span></span> <span data-ttu-id="99c70-106">優れた MDM ソリューションをビジネスの現場に導入することで、信頼性が高く分析可能なデータを一元的に管理できるようになるため、結果として、より的確な意思決定を行うことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="99c70-106">The result of a successful MDM solution is reliable, centralized data that can be analyzed, resulting in better business decisions.</span></span>

 <span data-ttu-id="99c70-107">ほとんどのビジネス ユーザーは適切なトレーニングを受けることで [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ソリューションを実装できるようになります。</span><span class="sxs-lookup"><span data-stu-id="99c70-107">With the right training, most business users should be able to implement a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] solution.</span></span> <span data-ttu-id="99c70-108">また、MDS を使用して、すべてのドメインの管理が可能になります。つまり、顧客、製品、またはアカウントのリスト管理のみに限定されるソリューションではありません。</span><span class="sxs-lookup"><span data-stu-id="99c70-108">In addition, you can use MDS to manage any domain; it's not specific to managing lists of customers, products, or accounts.</span></span> <span data-ttu-id="99c70-109">MDS の初回インストール時には、どのドメインの構造も含まれていません。必要なドメインを定義するには、そのモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="99c70-109">When MDS is first installed, it does not include the structure for any domains-you define the domains you need by creating models for them.</span></span>

 <span data-ttu-id="99c70-110">マスター データ サービスのその他の機能には、階層、きめ細かいセキュリティ、トランザクション、データのバージョン管理、ビジネス ルールなどがあります。</span><span class="sxs-lookup"><span data-stu-id="99c70-110">Other Master Data Services features include hierarchies, granular security, transactions, data versioning, and business rules.</span></span>

 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]<span data-ttu-id="99c70-111">には、次のコンポーネントとツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="99c70-111">includes the following components and tools:</span></span>

-   [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]<span data-ttu-id="99c70-112">: [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースと Web アプリケーションを作成および構成するために使用するツールです。</span><span class="sxs-lookup"><span data-stu-id="99c70-112">, a tool you use to create and configure [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] databases and web applications.</span></span>

-   [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]<span data-ttu-id="99c70-113">: 管理タスク (モデルやビジネス ルールの作成など) を実行するために使用し、データを更新するためにユーザーがアクセスする Web アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="99c70-113">, a web application you use to perform administrative tasks (like creating a model or business rule), and that users access to update data.</span></span>

-   <span data-ttu-id="99c70-114">MDSModelDeploy.exe: モデル オブジェクトとデータのパッケージを作成し、他の環境に配置できるようにするツールです。</span><span class="sxs-lookup"><span data-stu-id="99c70-114">MDSModelDeploy.exe, a tool you use to create packages of your model objects and data so you can deploy them to other environments.</span></span>

-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] <span data-ttu-id="99c70-115">Web サービス: 開発者が [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] のカスタム ソリューションを拡張または開発するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="99c70-115">web service, which developers can use to extend or develop custom solutions for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span>

-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]<span data-ttu-id="99c70-116">[!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]。データを管理したり、新しいエンティティや属性を作成したりするために使用します。</span><span class="sxs-lookup"><span data-stu-id="99c70-116">[!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)], which you use to manage data and create new entities and attributes.</span></span>

 <span data-ttu-id="99c70-117">MDS リソースの概要については、 [SQL Server マスターデータサービス Portal](https://go.microsoft.com/fwlink/?LinkID=214272)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99c70-117">For a summary of MDS resources, see the [SQL Server Master Data Services Portal](https://go.microsoft.com/fwlink/?LinkID=214272).</span></span>

|||
|-|-|
|<span data-ttu-id="99c70-118">**領域ごとのコンテンツの参照**</span><span class="sxs-lookup"><span data-stu-id="99c70-118">**Browse Content by Area**</span></span><br /> <span data-ttu-id="99c70-119">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[マスターデータサービスの概要](master-data-services-overview-mds.md)</span><span class="sxs-lookup"><span data-stu-id="99c70-119">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Master Data Services Overview](master-data-services-overview-mds.md)</span></span><br /><br /> <span data-ttu-id="99c70-120">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[マスターデータサービス機能とタスク](../../2014/master-data-services/master-data-services-features-and-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="99c70-120">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Master Data Services Features and Tasks](../../2014/master-data-services/master-data-services-features-and-tasks.md)</span></span><br /><br /> <span data-ttu-id="99c70-121">![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[テクニカルリファレンス (マスターデータサービス)](technical-reference-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="99c70-121">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Technical Reference (Master Data Services)](technical-reference-master-data-services.md)</span></span><br /><br /> <span data-ttu-id="99c70-122">![小ファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[開発者ガイド (マスターデータサービス)](develop/master-data-services-developer-documentation.md)</span><span class="sxs-lookup"><span data-stu-id="99c70-122">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Developer's Guide (Master Data Services)](develop/master-data-services-developer-documentation.md)</span></span>||


