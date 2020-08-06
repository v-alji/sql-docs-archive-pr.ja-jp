---
title: SetWindowsServiceIdentity メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 15d1b7fa5fc6d69a963785cdaf976c80623c47f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737686"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserver_configurationsetting"></a>SetWindowsServiceIdentity メソッド (WMI MSReportServer_ConfigurationSetting)
  レポート サーバーの Windows サービスを指定された Windows ユーザーとして実行させ、レポート サーバーを運用できるファイル システム権限をこのアカウントに与えます。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *UseBuiltInAccount*  
 指定したアカウントが組み込み Windows アカウントであるかどうかを示します。  
  
 *アカウント*  
 Windows サービスの実行に使用する "DOMAIN\alias" 形式の Windows アカウント。  
  
 *パスワード*  
 アカウントのパスワード。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>解説  
 *UseBuiltInAccount*パラメーターがに設定され、 `true` レポートサーバーが Microsoft または Windows XP で実行されている場合 [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] 、 *Name*、 *Domain*、および*Password*の各パラメーターの値は無視され、ローカルシステムアカウントが使用されます。  
  
 *UseBuiltInAccount*パラメーターがに設定され、 `true` レポートサーバーが Windows server 2003 で実行されている場合、*ドメイン*と*パスワード*のプロパティは無視され、名前フィールドには "指定" または "builtin\networkservice" または "Builtin\LocalService" のいずれかが含まれている必要があります。  
  
 SetWindowsServiceIdentity メソッドはレポート サーバーのインストール ディレクトリのファイルおよびフォルダーに対するファイル権限を設定します。  
  
 *Account*パラメーターで指定されたアカウントには、 `LogonAsService` Windows の権限が必要です。 このメソッドは、指定されたアカウントにこの権限を与えます。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
