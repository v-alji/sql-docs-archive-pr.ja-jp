---
title: ポリシー ベースの管理ポリシーのエクスポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, export policy
ms.assetid: f0001b33-9078-4432-8460-496736fb325a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 15f554aeeebfd47c3fa1ea13b100fbe6bcfcc055
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641630"
---
# <a name="export-a-policy-based-management-policy"></a>ポリシー ベースの管理ポリシーのエクスポート
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシー ベースの管理ポリシーをエクスポートする方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **以下を使用してポリシーをエクスポートするには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-export-a-policy"></a>ポリシーをエクスポートするには  
  
1.  オブジェクト エクスプローラーで、エクスポートするポリシー ベースの管理ポリシーを含むサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[管理]** フォルダーを展開します。  
  
3.  プラス記号をクリックして **[ポリシー管理]** を展開します。  
  
4.  プラス記号をクリックして **[ポリシー]** フォルダーを展開します。  
  
5.  エクスポートするポリシーを右クリックし、 **[ポリシーのエクスポート]** をクリックします。  
  
6.  **[ポリシーのエクスポート]** ダイアログ ボックスで、アドレス バーにファイルのパスと名前を入力します。 または、ダイアログ ボックスのナビゲーション ウィンドウでファイルの適切な場所を見つけ、 **[ファイル名]** ボックスに XML ファイルの名前を入力します。  
  
7.  完了したら、 **[保存]** をクリックします。  
  
  
