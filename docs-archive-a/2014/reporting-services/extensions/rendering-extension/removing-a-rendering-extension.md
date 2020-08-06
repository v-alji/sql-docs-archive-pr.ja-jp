---
title: 表示拡張機能の削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77a8a9ac44b35f338f978913985617e4f264ddb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641492"
---
# <a name="removing-a-rendering-extension"></a><span data-ttu-id="4343b-102">表示拡張機能の削除</span><span class="sxs-lookup"><span data-stu-id="4343b-102">Removing a Rendering Extension</span></span>
  <span data-ttu-id="4343b-103">表示拡張機能を削除するには [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 、 `Extension` **%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 にある rsreportserver.config ファイルから表示拡張機能の要素を削除するだけです。 \<Instance Name>\ Reporting Services\ReportServer**フォルダー。</span><span class="sxs-lookup"><span data-stu-id="4343b-103">To remove a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] rendering extension, simply remove the `Extension` element for your rendering extension from the rsreportserver.config file, located in **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<Instance Name>\Reporting Services\ReportServer** folder.</span></span> <span data-ttu-id="4343b-104">レポートサーバーだけでなくレポートデザイナーのエントリを作成した場合は、 `Extension` [Rsreportdesigner 構成ファイル](../../report-server/rsreportdesigner-configuration-file.md)からも要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="4343b-104">If you made entries for a Report Designer as well as a report server, remove the `Extension` element from the [RSReportDesigner Configuration File](../../report-server/rsreportdesigner-configuration-file.md) as well.</span></span> <span data-ttu-id="4343b-105">構成情報を削除した後は、表示拡張機能をコンポーネントに使用できません。</span><span class="sxs-lookup"><span data-stu-id="4343b-105">After the configuration information is removed, the rendering extension is no longer available to the component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4343b-106">参照</span><span class="sxs-lookup"><span data-stu-id="4343b-106">See Also</span></span>  
 <span data-ttu-id="4343b-107">[Reporting Services 構成ファイル](../../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="4343b-107">[Reporting Services Configuration Files](../../report-server/reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="4343b-108">[表示拡張機能の実装](implementing-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="4343b-108">[Implementing a Rendering Extension](implementing-a-rendering-extension.md) </span></span>  
 <span data-ttu-id="4343b-109">[表示拡張機能の概要](rendering-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="4343b-109">[Rendering Extensions Overview](rendering-extensions-overview.md) </span></span>  
 <span data-ttu-id="4343b-110">[IRenderingExtension インターフェイスの実装](implementing-the-irenderingextension-interface.md) </span><span class="sxs-lookup"><span data-stu-id="4343b-110">[Implementing the IRenderingExtension Interface](implementing-the-irenderingextension-interface.md) </span></span>  
 <span data-ttu-id="4343b-111">[拡張機能のセキュリティに関する考慮事項](../security-considerations-for-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="4343b-111">[Security Considerations for Extensions](../security-considerations-for-extensions.md) </span></span>  
 [<span data-ttu-id="4343b-112">表示拡張機能の配置</span><span class="sxs-lookup"><span data-stu-id="4343b-112">Deploying a Rendering Extension</span></span>](deploying-a-rendering-extension.md)  
  
  
