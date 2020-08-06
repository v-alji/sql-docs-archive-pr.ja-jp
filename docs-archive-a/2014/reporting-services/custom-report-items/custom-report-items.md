---
title: カスタム レポート アイテム | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- extending Reporting Services
- Reporting Services, extending
- custom report items
ms.assetid: 64dcaf2c-1af5-4937-8ff7-98f1ec3b367e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 86b819cb4d305e537a52a2e7f25cdfa3aefa5f9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741634"
---
# <a name="custom-report-items"></a><span data-ttu-id="02549-102">カスタム レポート アイテム</span><span class="sxs-lookup"><span data-stu-id="02549-102">Custom Report Items</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="02549-103">は、包括的な API により、エンタープライズ レポートの作成とパブリッシュ、セキュリティとサブスクリプションの管理、およびレポート機能の拡張を行う一連の豊富なツールを備えています。</span><span class="sxs-lookup"><span data-stu-id="02549-103">provides a rich set of tools for building and publishing enterprise reports, managing security and subscriptions, and extending the reporting functionality through a comprehensive API.</span></span> <span data-ttu-id="02549-104">レポートは、レポート定義言語 (RDL) と呼ばれる XML ベースの言語を使用して定義されます。</span><span class="sxs-lookup"><span data-stu-id="02549-104">Reports are defined using an XML-based language called Report Definition Language (RDL).</span></span> <span data-ttu-id="02549-105">RDL は、レイアウト、クエリ情報、およびレポートのアイテムの種類を説明する一連の命令を提供します。</span><span class="sxs-lookup"><span data-stu-id="02549-105">RDL provides a set of instructions that describe layout, query information, and item types for a report.</span></span> <span data-ttu-id="02549-106">RDL は、カスタム レポート アイテムを作成することによって拡張できます。</span><span class="sxs-lookup"><span data-stu-id="02549-106">It is possible to extend RDL by writing a custom report item.</span></span> <span data-ttu-id="02549-107">カスタム レポート アイテムは、実行時にレポート プロセッサによって呼び出される実行時コンポーネント、およびカスタム レポート アイテムをレポート デザイナーで使用できるようにするデザイン時コンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="02549-107">The custom report item consists of a run-time component, which is called by the report processor at run time, and a design-time component, which allows the custom report item to be available in Report Designer.</span></span>  
  
 <span data-ttu-id="02549-108">完全に実装されたカスタム レポート アイテムの例については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services の製品サンプル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02549-108">For a sample of a fully implemented custom report item, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="custom-report-item-scenarios"></a><span data-ttu-id="02549-109">カスタム レポート アイテムのシナリオ</span><span class="sxs-lookup"><span data-stu-id="02549-109">Custom Report Item Scenarios</span></span>  
 <span data-ttu-id="02549-110">開発者が開発したアプリケーションに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を統合する場合、RDL ではネイティブでサポートされていない機能が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="02549-110">Developers who need to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into their applications may require functionality that is not natively supported in RDL.</span></span> <span data-ttu-id="02549-111">たとえば、マップ コントロール、横一覧、縦一覧、および再ピボット可能なマトリックスなどです。</span><span class="sxs-lookup"><span data-stu-id="02549-111">This may include items such as: map controls, horizontal lists, columnar lists, and repivotable matrixes.</span></span> <span data-ttu-id="02549-112">こうした要件を満たすため、実行時カスタム レポート アイテム コンポーネントを開発し、アプリケーションと共に配布することができます。</span><span class="sxs-lookup"><span data-stu-id="02549-112">A run-time custom report item component can be developed and distributed with an application to fill this need.</span></span>  
  
 <span data-ttu-id="02549-113">ネイティブでサポートされていない機能の提供という目的以外にも、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に既に含まれているコントロールの代替バージョンを使用して、開発者が既存の機能を拡張する場合があります。</span><span class="sxs-lookup"><span data-stu-id="02549-113">In addition to providing functionality that isn't natively supported, some developers may want to extend existing functionality with alternative versions of controls that are already included with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="02549-114">このシナリオでは、開発者は、実行時コンポーネント、デザイン時コンポーネント、および必要に応じて既存のレポート アイテムをカスタム レポート アイテムに変換するデザイン時レポート アイテム変換コンポーネントという 3 種類のコンポーネントを提供します。</span><span class="sxs-lookup"><span data-stu-id="02549-114">In this scenario, a developer could provide three components: a run-time component, a design-time component, and a design-time report item conversion component that converts an existing report item into a custom report item on demand.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="02549-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="02549-115">In This Section</span></span>  
 [<span data-ttu-id="02549-116">カスタム レポート アイテムのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="02549-116">Custom Report Item Architecture</span></span>](custom-report-item-architecture.md)  
 <span data-ttu-id="02549-117">カスタム レポート アイテムを構成するコンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="02549-117">Describes the components that make up a custom report item.</span></span>  
  
 [<span data-ttu-id="02549-118">カスタム レポート アイテムの実装要件</span><span class="sxs-lookup"><span data-stu-id="02549-118">Custom Report Item Implementation Requirements</span></span>](custom-report-item-implementation-requirements.md)  
 <span data-ttu-id="02549-119">カスタム レポート アイテムを作成するための前提条件について説明します。</span><span class="sxs-lookup"><span data-stu-id="02549-119">Describes prerequisites for creating a custom report item.</span></span>  
  
 [<span data-ttu-id="02549-120">カスタム レポート アイテムの実行時コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="02549-120">Creating a Custom Report Item Run-Time Component</span></span>](creating-a-custom-report-item-run-time-component.md)  
 <span data-ttu-id="02549-121">カスタム レポート アイテムの実行時コンポーネントの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="02549-121">Describes how to create a custom report item run-time component.</span></span>  
  
 [<span data-ttu-id="02549-122">カスタム レポート アイテムのデザイン時コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="02549-122">Creating a Custom Report Item Design-Time Component</span></span>](creating-a-custom-report-item-design-time-component.md)  
 <span data-ttu-id="02549-123">カスタム レポート アイテムのデザイン時コンポーネントの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="02549-123">Describes how to create a custom report item design-time component.</span></span>  
  
 [<span data-ttu-id="02549-124">方法: カスタム レポート アイテムを配置する</span><span class="sxs-lookup"><span data-stu-id="02549-124">How to: Deploy a Custom Report Item</span></span>](how-to-deploy-a-custom-report-item.md)  
 <span data-ttu-id="02549-125">カスタム レポート アイテムの配置方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="02549-125">Describes how to deploy a custom report item.</span></span>  
  
 [<span data-ttu-id="02549-126">カスタム レポート アイテムのクラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="02549-126">Custom Report Item Class Libraries</span></span>](custom-report-item-class-libraries.md)  
 <span data-ttu-id="02549-127">`Microsoft.ReportDesigner` 名前空間のカスタム レポート アイテム インフラストラクチャのクラスと、マネージド ラッパー クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="02549-127">Describes the custom report item infrastructure classes and managed wrapper classes in the `Microsoft.ReportDesigner` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02549-128">参照</span><span class="sxs-lookup"><span data-stu-id="02549-128">See Also</span></span>  
 [<span data-ttu-id="02549-129">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="02549-129">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
