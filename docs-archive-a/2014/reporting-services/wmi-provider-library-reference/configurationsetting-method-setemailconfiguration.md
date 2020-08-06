---
title: SetEmailConfiguration メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEmailConfiguration method
ms.assetid: b40a2224-2c90-4d32-892f-1fe73a0591ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 19068d7d7fff8c31c455ef76e8d2c2caa26b743f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737729"
---
# <a name="setemailconfiguration-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="6f762-102">SetEmailConfiguration メソッド (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="6f762-102">SetEmailConfiguration Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="6f762-103">レポート サーバーが電子メール送信に使用する電子メール配信拡張機能を構成します。</span><span class="sxs-lookup"><span data-stu-id="6f762-103">Configures the e-mail delivery extension used by the report server to send e-mail.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f762-104">構文</span><span class="sxs-lookup"><span data-stu-id="6f762-104">Syntax</span></span>  
  
```vb  
Public Sub SetEmailConfiguration(ByVal SendUsingSMTPServer As Boolean, _  
    ByVal SMTPServer As String, ByVal SenderEmailAddress As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetEmailConfiguration (Boolean SendUsingSMTPServer,   
   string SMTPServer, string SenderEmailAddress,   
   out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f762-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6f762-105">Parameters</span></span>  
 <span data-ttu-id="6f762-106">*SendUsingSMTPServer*</span><span class="sxs-lookup"><span data-stu-id="6f762-106">*SendUsingSMTPServer*</span></span>  
 <span data-ttu-id="6f762-107">サーバーが電子メール送信に SMTP サーバーを使用するかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="6f762-107">A Boolean value indicating whether the server is to use the SMTP server to send email.</span></span> <span data-ttu-id="6f762-108">この値は、true にのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="6f762-108">This value can only be set to true.</span></span> <span data-ttu-id="6f762-109">既定値は false です。</span><span class="sxs-lookup"><span data-stu-id="6f762-109">Default value is false.</span></span>  
  
 <span data-ttu-id="6f762-110">*SMTPServer*</span><span class="sxs-lookup"><span data-stu-id="6f762-110">*SMTPServer*</span></span>  
 <span data-ttu-id="6f762-111">SMTP サーバーの名前または IP アドレスを含む文字列。</span><span class="sxs-lookup"><span data-stu-id="6f762-111">A string containing the name or IP address of an SMTP server.</span></span>  
  
 <span data-ttu-id="6f762-112">*SenderEmailAddress*</span><span class="sxs-lookup"><span data-stu-id="6f762-112">*SenderEmailAddress*</span></span>  
 <span data-ttu-id="6f762-113">レポート サーバーから送信された電子メールの 'From:' フィールドで使用された電子メール アドレス。</span><span class="sxs-lookup"><span data-stu-id="6f762-113">The e-mail address used in the 'From:' field for e-mails sent from the report server.</span></span>  
  
 <span data-ttu-id="6f762-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="6f762-114">*HRESULT*</span></span>  
 <span data-ttu-id="6f762-115">[out] 呼び出しの成功または失敗を示す値。</span><span class="sxs-lookup"><span data-stu-id="6f762-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f762-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="6f762-116">Return Value</span></span>  
 <span data-ttu-id="6f762-117">メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。</span><span class="sxs-lookup"><span data-stu-id="6f762-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="6f762-118">値 0 は、メソッド呼び出しが成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="6f762-118">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="6f762-119">0 以外の値は、エラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="6f762-119">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f762-120">解説</span><span class="sxs-lookup"><span data-stu-id="6f762-120">Remarks</span></span>  
 <span data-ttu-id="6f762-121">*Sendusing Smtpserver*パラメーターがに設定されている場合 `true` 、レポートサーバー構成ファイルの**sendusing**エントリは1に設定されます。</span><span class="sxs-lookup"><span data-stu-id="6f762-121">When the *SendUsingSMTPServer* parameter is set to `true`, the **SendUsing** entry in the report server configuration file is set to 1.</span></span> <span data-ttu-id="6f762-122">*Sendusing Smtpserver*がに設定されている場合 `false` 、 **sendusing**エントリは構成されません。</span><span class="sxs-lookup"><span data-stu-id="6f762-122">When *SendUsingSMTPServer* is set to `false`, the **SendUsing** entry is not configured.</span></span>  
  
 <span data-ttu-id="6f762-123">このメソッドでは、レポート サーバー構成ファイルの **SendUsing** エントリを 1 以外の値に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="6f762-123">This method does not provide a way for users to set the **SendUsing** entry in the report server configuration file to a value other than 1.</span></span> <span data-ttu-id="6f762-124">SMTP メール以外を使用するようにレポート サーバーを構成するには、構成ファイルを手動で編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f762-124">To configure the report server for anything other than SMTP mail, you must edit the configuration file manually.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f762-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="6f762-125">Requirements</span></span>  
 <span data-ttu-id="6f762-126">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f762-126">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f762-127">参照</span><span class="sxs-lookup"><span data-stu-id="6f762-127">See Also</span></span>  
 [<span data-ttu-id="6f762-128">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="6f762-128">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
