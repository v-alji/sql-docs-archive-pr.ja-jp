---
title: フェールオーバー クラスター インスタンスの IP アドレスの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- modifying IP addresses
- failover clustering [SQL Server], IP addresses
- IP addresses [SQL Server]
- clusters [SQL Server], IP addresses
ms.assetid: b685f400-cbfe-4c5d-a070-227a1123dae4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 45d3ef0b70282efd870e4a076663719c2549deaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640536"
---
# <a name="change-the-ip-address-of-a-failover-cluster-instance"></a>フェールオーバー クラスター インスタンスの IP アドレスの変更
  このトピックでは、フェールオーバー クラスター マネージャー スナップインを使用して、AlwaysOn フェールオーバー クラスター インスタンス (FCI) の IP アドレス リソースを変更する方法について説明します。 フェールオーバー クラスター マネージャー スナップインは、Windows Server フェールオーバー クラスタリング (WSFC) サービスのクラスター管理アプリケーションです。  
  
-   **作業を開始する準備:** [セキュリティ](#Security)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
 開始する前に、「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックのトピック: [フェールオーバー クラスタ リングをインストールする前に](../install/before-installing-failover-clustering.md)」を参照してください。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 FCI を保持または更新するには、FCI のすべてのノードにおいて、サービスとしてログオンする権限を持つローカル管理者である必要があります。  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> フェールオーバー クラスター マネージャー スナップインの使用  
 **FCI の IP アドレス リソースを変更するには**  
  
1.  フェールオーバー クラスター マネージャー スナップインを開きます。  
  
2.  左側のペインで、 **[サービスとアプリケーション]** ノードを展開し、FCI をクリックします。  
  
3.  右側のペインの **[サーバー名]** カテゴリの下で、SQL Server インスタンスを右クリックし、 **[プロパティ]** をクリックして **プロパティ** ダイアログ ボックスを開きます。  
  
4.  **[全般]** タブで、IP アドレス リソースを変更します。  
  
5.  **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
6.  右側のペインで、[SQL IP Address1 (フェールオーバー クラスターのインスタンス名)] を右クリックし、 **[オフラインにする]** をクリックします。 [SQL IP Address1 (フェールオーバー クラスターのインスタンス名)]、[SQL Network Name (フェールオーバー クラスターのインスタンス名)]、および [ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ] の状態が、[オンライン]、[オフライン待ち]、[オフライン] と変化していくのを確認できます。  
  
7.  右側のペインで、[ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]] を右クリックし、 **[オンラインにする]** をクリックします。 [SQL IP Address1 (フェールオーバー クラスターのインスタンス名)]、[SQL Network Name (フェールオーバー クラスターのインスタンス名)]、および [ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ] の状態が、[オフライン]、[オンライン待ち]、[オンライン] と変化していくのを確認できます。  
  
8.  フェールオーバー クラスター マネージャー スナップインを閉じます。  
  
  
