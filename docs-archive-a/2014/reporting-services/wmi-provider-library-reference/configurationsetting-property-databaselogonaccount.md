---
title: DatabaseLogonAccount プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonAccount
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonAccount property
ms.assetid: 55f2863f-1ac1-4519-b512-e7f11c0ea5ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f9e844ff1d1447bd5abfefad8e82939575c7f47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737680"
---
# <a name="databaselogonaccount-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="6f247-102">DatabaseLogonAccount プロパティ (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="6f247-102">DatabaseLogonAccount Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="6f247-103">レポート サーバーがレポート サーバー データベースへの接続に使用するログオン アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="6f247-103">Specifies the logon account that the report server uses when connecting to the report server database.</span></span> <span data-ttu-id="6f247-104">読み取り専用。</span><span class="sxs-lookup"><span data-stu-id="6f247-104">Read only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f247-105">構文</span><span class="sxs-lookup"><span data-stu-id="6f247-105">Syntax</span></span>  
  
```vb  
Public Dim DatabaseLogonAccount As String  
```  
  
```csharp  
public string DatabaseLogonAccount;  
```  
  
## <a name="property-values"></a><span data-ttu-id="6f247-106">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="6f247-106">Property Values</span></span>  
 <span data-ttu-id="6f247-107">ログオン アカウント名を表す `String` オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6f247-107">A `String` object that represents the logon account name.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="6f247-108">コード例</span><span class="sxs-lookup"><span data-stu-id="6f247-108">Example Code</span></span>  
 [<span data-ttu-id="6f247-109">MSReportServer_ConfigurationSetting クラス</span><span class="sxs-lookup"><span data-stu-id="6f247-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a><span data-ttu-id="6f247-110">解説</span><span class="sxs-lookup"><span data-stu-id="6f247-110">Remarks</span></span>  
 <span data-ttu-id="6f247-111">このプロパティの有効値は、 [DatabaseLogonType](configurationsetting-property-databaselogontype.md) プロパティの値によって異なります。</span><span class="sxs-lookup"><span data-stu-id="6f247-111">Valid values for this property will vary depending on the value of the [DatabaseLogonType](configurationsetting-property-databaselogontype.md) property.</span></span>  
  
 <span data-ttu-id="6f247-112">[Databaselogontype](configurationsetting-property-databaselogontype.md)プロパティがに設定されている場合、このプロパティは無視され `2 (Service)` ます。</span><span class="sxs-lookup"><span data-stu-id="6f247-112">This property is ignored if the [DatabaseLogonType](configurationsetting-property-databaselogontype.md) property is set to `2 (Service)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f247-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="6f247-113">Requirements</span></span>  
 <span data-ttu-id="6f247-114">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f247-114">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f247-115">参照</span><span class="sxs-lookup"><span data-stu-id="6f247-115">See Also</span></span>  
 [<span data-ttu-id="6f247-116">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="6f247-116">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
