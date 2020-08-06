---
title: カスタム レポート アイテムのアーキテクチャ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, architecture
ms.assetid: 2a88ea46-c9f8-4dd7-aad1-16de11da4f06
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a053eb55547da9030eebe9036667cca2e14606f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631663"
---
# <a name="custom-report-item-architecture"></a><span data-ttu-id="46e3e-102">カスタム レポート アイテムのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="46e3e-102">Custom Report Item Architecture</span></span>
  <span data-ttu-id="46e3e-103">カスタム レポート アイテムは、レポート定義言語 (RDL) の拡張機能です。開発者は、カスタム レポート アイテムを使用して、RDL ではネイティブでサポートされない機能を追加するか、既存のコントロールの機能を拡張することができます。</span><span class="sxs-lookup"><span data-stu-id="46e3e-103">A custom report item is an extension to the Report Definition Language (RDL) that allows developers to add functionality that's not natively supported in RDL or extend the functionality of existing controls.</span></span> <span data-ttu-id="46e3e-104">カスタム レポート アイテムには、2 つのメイン コンポーネントである、実行時コンポーネントとデザイン時コンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="46e3e-104">There are two main components to a custom report item: the run-time component and the design-time component.</span></span> <span data-ttu-id="46e3e-105">これらのコンポーネントは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] アセンブリとして実装され、CLS 準拠の言語で作成できます。</span><span class="sxs-lookup"><span data-stu-id="46e3e-105">These components are implemented as [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] assemblies, and can be written in any CLS-compliant language.</span></span>  
  
## <a name="the-run-time-component"></a><span data-ttu-id="46e3e-106">実行時コンポーネント</span><span class="sxs-lookup"><span data-stu-id="46e3e-106">The Run-Time Component</span></span>  
 <span data-ttu-id="46e3e-107">カスタム レポート アイテムの実行時コンポーネントは、実行時にレポート プロセッサにより呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="46e3e-107">The run-time component for a custom report item is called by the report processor at run time.</span></span> <span data-ttu-id="46e3e-108">実行時コンポーネントは実行時にレポート プロセッサから渡されたデータを受け取り、そのデータを処理し、表示されたカスタム レポート アイテムを含む画像を返します。</span><span class="sxs-lookup"><span data-stu-id="46e3e-108">The run-time component accepts data passed by the report processor at run time, processes this data, and returns an image containing the rendered custom report item.</span></span>  
  
 <span data-ttu-id="46e3e-109">![カスタム レポート アイテムの実行時コンポーネント](../../../2014/reporting-services/media/customreportitemrun-timecomponentarchitecture.gif "カスタム レポート アイテムの実行時コンポーネント")</span><span class="sxs-lookup"><span data-stu-id="46e3e-109">![Custom report item run-time component](../../../2014/reporting-services/media/customreportitemrun-timecomponentarchitecture.gif "Custom report item run-time component")</span></span>  
  
## <a name="the-design-time-component"></a><span data-ttu-id="46e3e-110">デザイン時コンポーネント</span><span class="sxs-lookup"><span data-stu-id="46e3e-110">The Design-Time Component</span></span>  
 <span data-ttu-id="46e3e-111">デザイン時コンポーネントを使用して、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のレポート デザイナーでカスタム レポート アイテムを定義および操作することができます。</span><span class="sxs-lookup"><span data-stu-id="46e3e-111">The design-time component allows the custom report item to be defined and manipulated in the Report Designer interface in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="46e3e-112">デザイン時コンポーネントは、デザイン環境でのカスタム レポート アイテムの表示およびプロパティを制御するいくつかのサブコントロールで構成されています。</span><span class="sxs-lookup"><span data-stu-id="46e3e-112">The design-time component consists of several sub-controls that control the appearance and properties of the custom report item in the design environment.</span></span>  
  
 <span data-ttu-id="46e3e-113">![カスタム レポート アイテムのデザイン時コンポーネント](../../../2014/reporting-services/media/customreportitemdesign-timecomponentarchitecture.gif "カスタム レポート アイテムのデザイン時コンポーネント")</span><span class="sxs-lookup"><span data-stu-id="46e3e-113">![Custom report item design-time component](../../../2014/reporting-services/media/customreportitemdesign-timecomponentarchitecture.gif "Custom report item design-time component")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46e3e-114">参照</span><span class="sxs-lookup"><span data-stu-id="46e3e-114">See Also</span></span>  
 <span data-ttu-id="46e3e-115">[カスタムレポートアイテムの実行時コンポーネントの作成](../custom-report-items/creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="46e3e-115">[Creating a Custom Report Item Run-Time Component](../custom-report-items/creating-a-custom-report-item-run-time-component.md) </span></span>  
 <span data-ttu-id="46e3e-116">[カスタムレポートアイテムのデザイン時コンポーネントの作成](../custom-report-items/creating-a-custom-report-item-design-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="46e3e-116">[Creating a Custom Report Item Design-Time Component](../custom-report-items/creating-a-custom-report-item-design-time-component.md) </span></span>  
 [<span data-ttu-id="46e3e-117">方法: カスタム レポート アイテムを配置する</span><span class="sxs-lookup"><span data-stu-id="46e3e-117">How to: Deploy a Custom Report Item</span></span>](../custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
