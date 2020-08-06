---
title: SecureConnectionLevel プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SecureConnectionLevel
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SecureConnectionLevel property
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5d1b3bccc8a7fee3899fa21208d83a718a33f5fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737632"
---
# <a name="secureconnectionlevel-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="81dad-102">SecureConnectionLevel プロパティ (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="81dad-102">SecureConnectionLevel Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="81dad-103">RSReportServer.config ファイルに指定された、セキュリティで保護された接続レベルを返します。</span><span class="sxs-lookup"><span data-stu-id="81dad-103">Returns the secure connection level specified in the RSReportServer.config file.</span></span> <span data-ttu-id="81dad-104">読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="81dad-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81dad-105">構文</span><span class="sxs-lookup"><span data-stu-id="81dad-105">Syntax</span></span>  
  
```vb  
Public Dim SecureConnectionLevel As Integer  
```  
  
```csharp  
public Integer SecureConnectionLevel;  
```  
  
## <a name="property-values"></a><span data-ttu-id="81dad-106">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="81dad-106">Property Values</span></span>  
 <span data-ttu-id="81dad-107">`Integer`セキュリティで保護された接続レベルを表す値。</span><span class="sxs-lookup"><span data-stu-id="81dad-107">An `Integer` value that represents the secure connection level.</span></span> <span data-ttu-id="81dad-108">この戻り値は、SSL が構成されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="81dad-108">The return values indicate that the SSL is either configured or not.</span></span> <span data-ttu-id="81dad-109">1 以上の値は、SSL がオンであることを示します。</span><span class="sxs-lookup"><span data-stu-id="81dad-109">A value of greater than or equal to 1 indicates that SSL is turned on.</span></span> <span data-ttu-id="81dad-110">値 0 は、SSL がオフであることを示します。</span><span class="sxs-lookup"><span data-stu-id="81dad-110">A value of 0 indicates that SSL is turned off.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="81dad-111">コード例</span><span class="sxs-lookup"><span data-stu-id="81dad-111">Example Code</span></span>  
 [<span data-ttu-id="81dad-112">MSReportServer_ConfigurationSetting クラス</span><span class="sxs-lookup"><span data-stu-id="81dad-112">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="81dad-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="81dad-113">Requirements</span></span>  
 <span data-ttu-id="81dad-114">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81dad-114">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81dad-115">参照</span><span class="sxs-lookup"><span data-stu-id="81dad-115">See Also</span></span>  
 [<span data-ttu-id="81dad-116">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="81dad-116">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
