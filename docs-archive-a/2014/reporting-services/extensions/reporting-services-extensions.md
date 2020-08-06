---
title: Reporting Services の拡張機能 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SQL Server Reporting Services, extending
- extensions [Reporting Services], about extensions
- SSIS, extending
- Reporting Services, extending
- extensions [Reporting Services]
ms.assetid: 2bf17ae4-2292-4a58-a1f0-56e99abd9b69
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7ac942147c75424dae46d9a8e35dc57fba50755f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641486"
---
# <a name="reporting-services-extensions"></a><span data-ttu-id="364f5-102">Reporting Services の拡張機能</span><span class="sxs-lookup"><span data-stu-id="364f5-102">Reporting Services Extensions</span></span>
  <span data-ttu-id="364f5-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のモジュール式アーキテクチャは、拡張性を考慮して設計されています。</span><span class="sxs-lookup"><span data-stu-id="364f5-103">The modular architecture of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is designed for extensibility.</span></span> <span data-ttu-id="364f5-104">マネージド コード API を使用して、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の多くのコンポーネントで使用される拡張機能を容易に開発、インストール、および管理できます。</span><span class="sxs-lookup"><span data-stu-id="364f5-104">A managed code API is available so that you can easily develop, install, and manage extensions consumed by many [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components.</span></span> <span data-ttu-id="364f5-105">プライベートまたは共有のアセンブリを [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] を使用して作成し、変化するご自分のビジネス要件に応じて新しい [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="364f5-105">You can create private or shared assemblies using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] and add new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] functionality to meet your evolving business needs.</span></span>  
  
 <span data-ttu-id="364f5-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のユニークな拡張可能アーキテクチャによって、開発者は、製品とそのコンポーネントの特定の機能を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="364f5-106">The unique extensibility architecture of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enables developers to extend specific features of the product and its components.</span></span> <span data-ttu-id="364f5-107">現在では、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のデータ処理機能を拡張するために幅広いサポートがあります。</span><span class="sxs-lookup"><span data-stu-id="364f5-107">Currently, broad support exists for extending the data processing capabilities of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="364f5-108">データ処理 API では、使い慣れた [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーのコンストラクトと規約が採用されているので、開発者は、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に新しいデータ処理を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="364f5-108">The data processing API includes familiar, [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider constructs and conventions that enable developers to build additional data processing into [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="364f5-109">これらのデータ処理拡張機能によって、レポート サーバーとレポート デザイナーの両方に機能を追加し、カスタム データをレポートにシームレスに統合できます。</span><span class="sxs-lookup"><span data-stu-id="364f5-109">These data processing extensions add functionality to both the Report Server and Report Designer, enabling seamless integration of custom data into reports.</span></span>  
  
 <span data-ttu-id="364f5-110">配信拡張機能もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="364f5-110">Another supported extension is the delivery extension.</span></span> <span data-ttu-id="364f5-111">配信 API は [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] アーキテクチャと完全に統合されているので、さまざまな配信メカニズムを使用して、レポート通知をユーザーに送信できます。</span><span class="sxs-lookup"><span data-stu-id="364f5-111">The delivery API is fully integrated with the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] architecture, enabling a wide variety of delivery mechanisms to be used when sending report notifications to users.</span></span> <span data-ttu-id="364f5-112">レポート サーバーを拡張してカスタム配信をユーザーに提供できます。レポート マネージャーのサブスクリプション管理ページを拡張して、カスタム配信拡張機能を使用したサブスクリプションを可能にします。</span><span class="sxs-lookup"><span data-stu-id="364f5-112">You can extend the Report Server to provide custom delivery to users and you can extend the subscription management pages of Report Manager to enable subscriptions that use custom delivery extensions.</span></span>  
  
 <span data-ttu-id="364f5-113">別のレポート サーバー拡張機能であるレポート定義カスタマイズ拡張機能 (RDCE) では、レポート定義を処理エンジンに渡す前に動的にカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="364f5-113">Another report server extension, Report Definition Customization Extension (RDCE), can dynamically customize a report definition before it is passed to the processing engine.</span></span> <span data-ttu-id="364f5-114">レポートは、ユーザーや言語などの要因に基づいてカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="364f5-114">You might customize reports based on factors such as users or languages.</span></span> <span data-ttu-id="364f5-115">たとえば、部署のマネージャーやメンバーなどのユーザーごとに異なるビューを実装したり、フランス語やアラビア語では異なるレイアウトで表示されるようにレポートをカスタマイズしたりできます。</span><span class="sxs-lookup"><span data-stu-id="364f5-115">For example, you might want to implement different views for various users such as managers or members of a department, or you might want to customize a report to have a different layout when it is rendered in French or Arabic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="364f5-116">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="364f5-116">In This Section</span></span>  
 [<span data-ttu-id="364f5-117">拡張機能のセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="364f5-117">Security Considerations for Extensions</span></span>](security-considerations-for-extensions.md)  
 <span data-ttu-id="364f5-118">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 拡張機能の開発と配置に関連するセキュリティ上の問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="364f5-118">Describes security issues related to developing and deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] extensions.</span></span>  
  
 [<span data-ttu-id="364f5-119">データ処理拡張機能の実装</span><span class="sxs-lookup"><span data-stu-id="364f5-119">Implementing a Data Processing Extension</span></span>](data-processing/implementing-a-data-processing-extension.md)  
 <span data-ttu-id="364f5-120">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のデータ処理拡張機能を実装するための要件と手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="364f5-120">Describes the requirements and steps for implementing a data processing extension for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="364f5-121">配信拡張機能の実装</span><span class="sxs-lookup"><span data-stu-id="364f5-121">Implementing a Delivery Extension</span></span>](delivery-extension/implementing-a-delivery-extension.md)  
 <span data-ttu-id="364f5-122">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の配信拡張機能を実装するための要件と手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="364f5-122">Describes the requirements and steps for implementing a delivery extension for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="364f5-123">表示拡張機能の実装</span><span class="sxs-lookup"><span data-stu-id="364f5-123">Implementing a Rendering Extension</span></span>](rendering-extension/implementing-a-rendering-extension.md)  
 <span data-ttu-id="364f5-124">表示拡張機能の開発の概要が記載されています。</span><span class="sxs-lookup"><span data-stu-id="364f5-124">Contains an introduction to developing rendering extensions.</span></span>  
  
 [<span data-ttu-id="364f5-125">セキュリティ拡張機能の実装</span><span class="sxs-lookup"><span data-stu-id="364f5-125">Implementing a Security Extension</span></span>](security-extension/implementing-a-security-extension.md)  
 <span data-ttu-id="364f5-126">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のセキュリティ拡張機能を実装するための要件と手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="364f5-126">Describes the requirements and steps for implementing a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] security extension.</span></span>  
  
 [<span data-ttu-id="364f5-127">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="364f5-127">Reporting Services Extension Library</span></span>](reporting-services-extension-library.md)  
 <span data-ttu-id="364f5-128">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の拡張可能な機能を対象とした拡張機能 API ライブラリのプログラミング リファレンスです。</span><span class="sxs-lookup"><span data-stu-id="364f5-128">Contains the programming reference for the extension API library for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] extensibility features.</span></span>  
  
  
