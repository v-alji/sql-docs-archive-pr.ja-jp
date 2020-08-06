---
title: Reporting Services WMI プロバイダー ライブラリ リファレンス (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider Library
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services], library
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a98ca22f9d34627e484a698dcf540b31808d07e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639853"
---
# <a name="reporting-services-wmi-provider-library-reference-ssrs"></a><span data-ttu-id="18acb-102">Reporting Services WMI プロバイダー ライブラリ リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="18acb-102">Reporting Services WMI Provider Library Reference (SSRS)</span></span>
  <span data-ttu-id="18acb-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) プロバイダーは WMI 操作をサポートし、レポート サーバーとレポート マネージャーの設定を修正するスクリプトとコードの記述を可能にします。</span><span class="sxs-lookup"><span data-stu-id="18acb-103">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) provider supports WMI operations that enable you to write scripts and code to modify settings of the report server and Report Manager.</span></span>  
  
 <span data-ttu-id="18acb-104">たとえば、レポート サーバーがレポート サーバー データベースと接続するときに統合セキュリティを使用するかどうかを変更する場合は、MSReportServer_ConfigurationSetting クラスのインスタンスを作成して、レポート サーバー インスタンスの DatabaseIntegratedSecurity プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="18acb-104">For example, if you want to change whether integrated security is used when the report server connects to the report server database, create an instance of the MSReportServer_ConfigurationSetting class and use the DatabaseIntegratedSecurity property of the of the report server instance.</span></span> <span data-ttu-id="18acb-105">次の表のクラスは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントを表しています。</span><span class="sxs-lookup"><span data-stu-id="18acb-105">The classes shown in the following table represent [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components.</span></span> <span data-ttu-id="18acb-106">これらのクラスは、 [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] 名前空間または [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] 名前空間で定義されています。</span><span class="sxs-lookup"><span data-stu-id="18acb-106">The classes are defined in either the [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] or the [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] namespaces.</span></span> <span data-ttu-id="18acb-107">各クラスは読み取り操作と書き込み操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="18acb-107">Each of the classes support read and write operations.</span></span> <span data-ttu-id="18acb-108">作成操作はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="18acb-108">Create operations are not supported.</span></span>  
  
## <a name="classes"></a><span data-ttu-id="18acb-109">クラス</span><span class="sxs-lookup"><span data-stu-id="18acb-109">Classes</span></span>  
 [<span data-ttu-id="18acb-110">MSReportServer_Instance クラス</span><span class="sxs-lookup"><span data-stu-id="18acb-110">MSReportServer_Instance Class</span></span>](msreportserver-instance-class.md)  
 <span data-ttu-id="18acb-111">インストールされているレポート サーバーに接続するための基本情報をクライアントに提供します。</span><span class="sxs-lookup"><span data-stu-id="18acb-111">Provides basic information required for a client to connect to an installed report server.</span></span>  
  
 [<span data-ttu-id="18acb-112">MSReportServer_ConfigurationSetting クラス</span><span class="sxs-lookup"><span data-stu-id="18acb-112">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
 <span data-ttu-id="18acb-113">レポート サーバー インスタンスのインストール パラメーターとランタイム パラメーターを表します。</span><span class="sxs-lookup"><span data-stu-id="18acb-113">Represents the installation and run-time parameters of a report server instance.</span></span> <span data-ttu-id="18acb-114">これらのパラメーターはレポート サーバーの構成ファイルに格納されています。</span><span class="sxs-lookup"><span data-stu-id="18acb-114">These parameters are stored in the configuration file for the report server.</span></span>  
  
 <span data-ttu-id="18acb-115">WMI 操作の詳細については、sdk に付属の WMI SDK ドキュメントを参照してください [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="18acb-115">For more information about WMI operations, see the WMI SDK documentation included with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18acb-116">参照</span><span class="sxs-lookup"><span data-stu-id="18acb-116">See Also</span></span>  
 <span data-ttu-id="18acb-117">[Reporting Services WMI プロバイダーにアクセスする](../tools/access-the-reporting-services-wmi-provider.md) </span><span class="sxs-lookup"><span data-stu-id="18acb-117">[Access the Reporting Services WMI Provider](../tools/access-the-reporting-services-wmi-provider.md) </span></span>  
 [<span data-ttu-id="18acb-118">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="18acb-118">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
