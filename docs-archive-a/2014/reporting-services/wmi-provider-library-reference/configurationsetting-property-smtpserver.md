---
title: SMTPServer プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SMTPServer
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SMTPServer property
ms.assetid: 8bcceeba-e1a0-44ef-bda1-600c6925e1db
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b706834c80fa0ff126d35beffbfdc84ef92cefe6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737614"
---
# <a name="smtpserver-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="fb07d-102">SMTPServer プロパティ (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="fb07d-102">SMTPServer Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="fb07d-103">レポート サーバー構成ファイルから SMTP サーバー プロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="fb07d-103">Gets the SMTP server property from the report server configuration file.</span></span> <span data-ttu-id="fb07d-104">読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="fb07d-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb07d-105">構文</span><span class="sxs-lookup"><span data-stu-id="fb07d-105">Syntax</span></span>  
  
```vb  
Public Dim SMTPServer As String  
```  
  
```csharp  
public string SMTPServer;  
```  
  
## <a name="property-values"></a><span data-ttu-id="fb07d-106">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="fb07d-106">Property Values</span></span>  
 <span data-ttu-id="fb07d-107">RSReportServer.config ファイルから取得した `String` プロパティ値を含む、読み取り専用の `SMTPServer` オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fb07d-107">A read-only `String` object containing the value of the `SMTPServer` property from the RSReportServer.config file.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="fb07d-108">コード例</span><span class="sxs-lookup"><span data-stu-id="fb07d-108">Example Code</span></span>  
 [<span data-ttu-id="fb07d-109">MSReportServer_ConfigurationSetting クラス</span><span class="sxs-lookup"><span data-stu-id="fb07d-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="fb07d-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="fb07d-110">Requirements</span></span>  
 <span data-ttu-id="fb07d-111">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb07d-111">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb07d-112">参照</span><span class="sxs-lookup"><span data-stu-id="fb07d-112">See Also</span></span>  
 [<span data-ttu-id="fb07d-113">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="fb07d-113">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
