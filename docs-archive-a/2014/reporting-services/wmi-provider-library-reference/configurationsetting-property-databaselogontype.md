---
title: DatabaseLogonType プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonType
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3bb5a4149c29fb7532b7140a2616dd856e6db2b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737663"
---
# <a name="databaselogontype-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="af6bf-102">DatabaseLogonType プロパティ (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="af6bf-102">DatabaseLogonType Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="af6bf-103">レポート サーバーが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows サービス アカウント、Windows ユーザー アカウント、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのうちどれを使用してレポート サーバー データベースにアクセスするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="af6bf-103">Specifies whether the report server uses a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows service account, a Windows user account, or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to access the report server database.</span></span> <span data-ttu-id="af6bf-104">読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="af6bf-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af6bf-105">構文</span><span class="sxs-lookup"><span data-stu-id="af6bf-105">Syntax</span></span>  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a><span data-ttu-id="af6bf-106">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="af6bf-106">Property Values</span></span>  
 <span data-ttu-id="af6bf-107">ログインの種類を表す `integer` オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="af6bf-107">An `integer` object that represents the login type.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="af6bf-108">コード例</span><span class="sxs-lookup"><span data-stu-id="af6bf-108">Example Code</span></span>  
 [<span data-ttu-id="af6bf-109">MSReportServer_ConfigurationSetting クラス</span><span class="sxs-lookup"><span data-stu-id="af6bf-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a><span data-ttu-id="af6bf-110">解説</span><span class="sxs-lookup"><span data-stu-id="af6bf-110">Remarks</span></span>  
 <span data-ttu-id="af6bf-111">値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="af6bf-111">Values are:</span></span>  
  
-   <span data-ttu-id="af6bf-112">Windows ログインの場合は 0</span><span class="sxs-lookup"><span data-stu-id="af6bf-112">0 for Windows login</span></span>  
  
-   <span data-ttu-id="af6bf-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの場合は 1</span><span class="sxs-lookup"><span data-stu-id="af6bf-113">1 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login</span></span>  
  
-   <span data-ttu-id="af6bf-114">サービスとしてログインする場合は 2</span><span class="sxs-lookup"><span data-stu-id="af6bf-114">2 to log in as a service</span></span>  
  
 <span data-ttu-id="af6bf-115">0 (Windows) を指定する場合は、 [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) プロパティの値を、有効な Windows ユーザー アカウントに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af6bf-115">If you specify 0 (Windows), you must set the value in the [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) property to a corresponding a valid Windows user account.</span></span>  
  
 <span data-ttu-id="af6bf-116">1 (SQL Server) を指定する場合は、 [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) の値が有効な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="af6bf-116">If you specify 1 (SQL Server), make sure the value of the [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) corresponds to a valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
 <span data-ttu-id="af6bf-117">2 (Windows サービス) を指定する場合、レポート サーバーは [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アカウントと Windows サービス アカウントを使用してレポート サーバー データベースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="af6bf-117">If you specify 2 (Windows service), the report server uses an [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] account and the Windows service account to access the report server database.</span></span> <span data-ttu-id="af6bf-118">DatabaseLogonAccount プロパティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="af6bf-118">The DatabaseLogonAccount property is ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af6bf-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="af6bf-119">Requirements</span></span>  
 <span data-ttu-id="af6bf-120">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af6bf-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af6bf-121">参照</span><span class="sxs-lookup"><span data-stu-id="af6bf-121">See Also</span></span>  
 [<span data-ttu-id="af6bf-122">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="af6bf-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
