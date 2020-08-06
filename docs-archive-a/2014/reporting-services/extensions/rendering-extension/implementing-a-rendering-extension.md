---
title: 表示拡張機能の実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03deb7c818de8d875f69b585ae6015fc178e707d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641494"
---
# <a name="implementing-a-rendering-extension"></a><span data-ttu-id="4cf22-102">表示拡張機能の実装</span><span class="sxs-lookup"><span data-stu-id="4cf22-102">Implementing a Rendering Extension</span></span>
  <span data-ttu-id="4cf22-103">表示拡張機能は、レポート サーバーのコンポーネントまたはモジュールで、レポートのデータとレイアウト情報をデバイス固有の形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="4cf22-103">A rendering extension is a component or module of a report server that transforms report data and layout information into a device-specific format.</span></span> <span data-ttu-id="4cf22-104">SQL Server Reporting Services には 6 種類の表示拡張機能 (HTML、Excel、Word、CSV (Text)、XML、Image、PDF) があります。</span><span class="sxs-lookup"><span data-stu-id="4cf22-104">SQL Server Reporting Services includes six rendering extensions: HTML, Excel, Word, CSV or Text, XML, Image, and PDF.</span></span> <span data-ttu-id="4cf22-105">追加の表示拡張機能を作成して、他の形式でレポートを生成できます。</span><span class="sxs-lookup"><span data-stu-id="4cf22-105">You can create additional rendering extensions to generate reports in other formats.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cf22-106">どの表示拡張機能を利用できるかは、RSReportServer.config ファイルのインストール済み拡張機能の一覧で確認できます。</span><span class="sxs-lookup"><span data-stu-id="4cf22-106">To determine which rendering extensions are available, you can view the list of installed extensions in the RSReportServer.config file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4cf22-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4cf22-107">In This Section</span></span>  
 [<span data-ttu-id="4cf22-108">表示拡張機能の概要</span><span class="sxs-lookup"><span data-stu-id="4cf22-108">Rendering Extensions Overview</span></span>](rendering-extensions-overview.md)  
 <span data-ttu-id="4cf22-109">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のカスタム表示機能の記述方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4cf22-109">Introduces how to write a custom rendering extension for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="4cf22-110">IRenderingExtension インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="4cf22-110">Implementing the IRenderingExtension Interface</span></span>](implementing-the-irenderingextension-interface.md)  
 <span data-ttu-id="4cf22-111">表示拡張機能の属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="4cf22-111">Describes the attributes of a rendering extension.</span></span>  
  
 [<span data-ttu-id="4cf22-112">表示拡張機能の配置</span><span class="sxs-lookup"><span data-stu-id="4cf22-112">Deploying a Rendering Extension</span></span>](deploying-a-rendering-extension.md)  
 <span data-ttu-id="4cf22-113">レポート サーバーに表示拡張機能を配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4cf22-113">Describes how to deploy a rendering extension on a report server.</span></span>  
  
 [<span data-ttu-id="4cf22-114">表示拡張機能の削除</span><span class="sxs-lookup"><span data-stu-id="4cf22-114">Removing a Rendering Extension</span></span>](removing-a-rendering-extension.md)  
 <span data-ttu-id="4cf22-115">レポート サーバーから表示拡張機能を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4cf22-115">Describes how to remove a rendering extension from a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf22-116">参照</span><span class="sxs-lookup"><span data-stu-id="4cf22-116">See Also</span></span>  
 <span data-ttu-id="4cf22-117">[Reporting Services の拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="4cf22-117">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="4cf22-118">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="4cf22-118">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
