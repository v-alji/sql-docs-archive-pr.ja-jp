---
title: レポートサーバーへの直接参照 (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ab4d146bba4bd87de56b30ad100b57f79eb68de3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645369"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a>レポート サーバーの直接参照 (アップグレード アドバイザー)
  アップグレードアドバイザーによって、の現在のインストール [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がレポートサーバーの仮想ディレクトリを直接参照していることが検出されました。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 アップグレードアドバイザーによって、の現在のインストール [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がレポートサーバーの仮想ディレクトリ ( **http:// \<server name> /ReportServer**など) を直接参照していることが検出されました。 このような直接参照は現在のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ではサポートされていません。  
  
> [!NOTE]  
>  この規則は警告であり、アップグレードはブロックされません。  
  
## <a name="corrective-action"></a>修正措置  
 ドキュメントライブラリの SharePoint ユーザーインターフェイスを使用して参照するか、 **http:// \<server name> /SharePoint サイト>/_vti_bin/reportserver**を使用します。  
  
  
