---
title: SetExtendedProtectionSettings メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ee937747b74bcf8d53012721b4be5bfca04185df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737728"
---
# <a name="setextendedprotectionsettings-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="9c13c-102">SetExtendedProtectionSettings メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="9c13c-102">SetExtendedProtectionSettings Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="9c13c-103">SetExtendedProtectionSettings メソッドは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の構成ファイル (RSReportServer.config) で RSWindowsExtendedProtectionLevel プロパティと RSWindowsExtendedProtectionScenario プロパティを設定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="9c13c-103">The SetExtendedProtectionSettings method is used to set the RSWindowsExtendedProtectionLevel and the RSWindowsExtendedProtectionScenario properties in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration file RSReportServer.config.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c13c-104">構文</span><span class="sxs-lookup"><span data-stu-id="9c13c-104">Syntax</span></span>  
  
```vb  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c13c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c13c-105">Parameters</span></span>  
 <span data-ttu-id="9c13c-106">*ExtendedProtectionLevel*</span><span class="sxs-lookup"><span data-stu-id="9c13c-106">*ExtendedProtectionLevel*</span></span>  
 <span data-ttu-id="9c13c-107">RSRreportserver.config ファイルで RSWindowsExtendedProtectionLevel を設定します。</span><span class="sxs-lookup"><span data-stu-id="9c13c-107">Sets the RSWindowsExtendedProtectionLevel in the RSRreportserver.config file.</span></span> <span data-ttu-id="9c13c-108">この必須の値では大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="9c13c-108">The required value is not case sensitive.</span></span>  
  
 <span data-ttu-id="9c13c-109">有効な値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9c13c-109">The following list shows valid values:</span></span>  
  
 `"Off | Allow | Require"`  
  
 <span data-ttu-id="9c13c-110">*ExtendedProtectionScenario*</span><span class="sxs-lookup"><span data-stu-id="9c13c-110">*ExtendedProtectionScenario*</span></span>  
 <span data-ttu-id="9c13c-111">RSReportserver.config ファイルで RSWindowsExtendedProtectionScenario を設定します。</span><span class="sxs-lookup"><span data-stu-id="9c13c-111">Sets the RSWindowsExtendedProtectionScenario in the RSReportserver.config file.</span></span> <span data-ttu-id="9c13c-112">この必須の値では大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="9c13c-112">The required value is not case sensitive.</span></span>  
  
 <span data-ttu-id="9c13c-113">有効な値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9c13c-113">The following list shows valid values:</span></span>  
  
 `"Any" | "Proxy" | "Direct"`  
  
## <a name="remarks"></a><span data-ttu-id="9c13c-114">解説</span><span class="sxs-lookup"><span data-stu-id="9c13c-114">Remarks</span></span>  
 <span data-ttu-id="9c13c-115">RSWindowsExtendedProtectionLevel プロパティと RSWindowsExtendedProtectionScenario プロパティは、RSReportServer.config ファイルの AuthenticationTypes に RSWindowNTLM、RSWindowsNegotiate、または RSWindowsKerberos が含まれている場合に適用されます。</span><span class="sxs-lookup"><span data-stu-id="9c13c-115">The RSWindowsExtendedProtectionLevel and the RSWindowsExtendedProtectionScenario properties apply when the AuthenticationTypes in the RSReportServer.config file include RSWindowNTLM, RSWindowsNegotiate, or RSWindowsKerberos.</span></span> <span data-ttu-id="9c13c-116">これらのプロパティの設定は、レポート サーバーでのユーザーとクライアント ソフトウェアの認証方法に影響します。</span><span class="sxs-lookup"><span data-stu-id="9c13c-116">Setting these properties affects how users and client software authenticate with a report server.</span></span> <span data-ttu-id="9c13c-117">ExtendedProtectionLevel を `Allow` または `Require` に設定する前に、拡張保護に関するドキュメントを読むことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9c13c-117">It is recommended that you read the documentation for extended protection before setting ExtendedProtectionLevel to either `Allow` or `Require`.</span></span>  
  
 <span data-ttu-id="9c13c-118">ExtendedProtectionLevel を設定するには、ユーザーはレポート サーバーの BUILTIN\Administrators グループのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c13c-118">To set the ExtendedProtectionLevel, the user must be a member of the BUILTIN\Administrators group on the report server.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c13c-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="9c13c-119">Requirements</span></span>  
 <span data-ttu-id="9c13c-120">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c13c-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c13c-121">参照</span><span class="sxs-lookup"><span data-stu-id="9c13c-121">See Also</span></span>  
 <span data-ttu-id="9c13c-122">[RSWindowsExtendedProtectionScenario プロパティ (WMI MSReportServer_ConfigurationSetting)](rswindowsextendedprotectionscenario-property.md) </span><span class="sxs-lookup"><span data-stu-id="9c13c-122">[RSWindowsExtendedProtectionScenario Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md) </span></span>  
 <span data-ttu-id="9c13c-123">[RSWindowsExtendedProtectionLevel プロパティ (WMI MSReportServer_ConfigurationSetting)](rswindowsextendedprotectionlevel-property.md) </span><span class="sxs-lookup"><span data-stu-id="9c13c-123">[RSWindowsExtendedProtectionLevel Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md) </span></span>  
 <span data-ttu-id="9c13c-124">[Reporting Services での認証の拡張保護](../security/extended-protection-for-authentication-with-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="9c13c-124">[Extended Protection for Authentication with Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md) </span></span>  
 [<span data-ttu-id="9c13c-125">RSReportServer 構成ファイル</span><span class="sxs-lookup"><span data-stu-id="9c13c-125">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
