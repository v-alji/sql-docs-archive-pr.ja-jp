---
title: データベース エンジンがインストールされ開始されているかどうかの確認 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, determining if installed
- verifying Database Engine installation
- viewing Database Engine installation
- installed Database Engine verification [SQL Server]
ms.assetid: babb02e4-3521-4b75-b5df-e09205594375
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0a912cf4a89f208543605cc84f480b63955214ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740417"
---
# <a name="determine-whether-the-database-engine-is-installed-and-started"></a><span data-ttu-id="8086f-102">データベース エンジンがインストールされ開始されているかどうかの確認</span><span class="sxs-lookup"><span data-stu-id="8086f-102">Determine Whether the Database Engine Is Installed and Started</span></span>
  <span data-ttu-id="8086f-103">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインストールが成功すると、ファイルがファイル システムにインストールされ、レジストリのエントリが作成されて、ツールがいくつかインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8086f-103">A successful installation of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] installs files to the file system, creates entries in the registry, and installs several tools.</span></span> <span data-ttu-id="8086f-104">このトピックでは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 構成マネージャーを使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がインストールされて起動されているかどうかを確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8086f-104">This topic describes how to determine whether the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is installed and started in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8086f-105">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="8086f-105">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="how-to-view-and-start-the-database-engine-by-using-sql-server-configuration-manager"></a><span data-ttu-id="8086f-106">SQL Server 構成マネージャーを使用してデータベース エンジンを表示および開始する方法</span><span class="sxs-lookup"><span data-stu-id="8086f-106">How to view and start the Database Engine by using SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="8086f-107">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** 、 **[構成ツール]** の順にポイントし、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8086f-107">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
     <span data-ttu-id="8086f-108">**[スタート]** メニューにこれらのエントリがない場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が正しくインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="8086f-108">If you do not have these entries on the **Start** menu, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not correctly installed.</span></span> <span data-ttu-id="8086f-109">セットアップを実行して、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]をインストールします。</span><span class="sxs-lookup"><span data-stu-id="8086f-109">Run Setup to install the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="8086f-110">**[SQL Server 構成マネージャー]** の左側のペインで、 **[SQL Server のサービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8086f-110">In **SQL Server Configuration Manager**, on the left pane, click **SQL Server Services**.</span></span> <span data-ttu-id="8086f-111">右側のペインには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に関連するサービスがいくつか表示されます。</span><span class="sxs-lookup"><span data-stu-id="8086f-111">The right pane lists several services that are related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8086f-112">[!INCLUDE[ssDE](../../includes/ssde-md.md)] がインストールされている場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスは **[SQL Server (MSSQLSERVER)]** と表示されるか (これが既定のインスタンスの場合)、 **[SQL Server (** \<*instance_name*> **)]** と表示されます ([!INCLUDE[ssDE](../../includes/ssde-md.md)] が名前付きインスタンスとしてインストールされている場合)。</span><span class="sxs-lookup"><span data-stu-id="8086f-112">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is installed, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service is listed as **SQL Server (MSSQLSERVER)** if it is the default instance; or **SQL Server (**\<*instance_name*>**)**, if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is installed as a named instance.</span></span> <span data-ttu-id="8086f-113">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] はインスタンス名が変更されない限り、 **SQLEXPRESS**という名前の名前付きインスタンスとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8086f-113">Unless the instance name is changed, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs as a named instance with the name **SQLEXPRESS**.</span></span> <span data-ttu-id="8086f-114">緑の三角形のアイコンは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] が実行中であることを示します。</span><span class="sxs-lookup"><span data-stu-id="8086f-114">A green triangle icon indicates that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is running.</span></span> <span data-ttu-id="8086f-115">赤い四角形のアイコンは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] が停止していることを示します。</span><span class="sxs-lookup"><span data-stu-id="8086f-115">A red square icon indicates that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is stopped.</span></span>  
  
3.  <span data-ttu-id="8086f-116">[!INCLUDE[ssDE](../../includes/ssde-md.md)]を開始するには、右側のペインで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]を右クリックして、 **[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8086f-116">To start the [!INCLUDE[ssDE](../../includes/ssde-md.md)], in the right pane, right-click the [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Start**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8086f-117">ユーザーは、セットアップ時に、プログラム ファイルとデータベース ファイルをインストールする場所を選択できます。</span><span class="sxs-lookup"><span data-stu-id="8086f-117">During setup, the user can select a location in which to install the program files and the database files.</span></span> <span data-ttu-id="8086f-118">ユーザーが既定の場所をそのまま使用すると、ファイルは [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] および C:\Program Files\Microsoft SQL Server\MSSQL.*x*( *x* は番号) にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8086f-118">If the user accepts the default location, the files are installed to [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] and C:\Program Files\Microsoft SQL Server\MSSQL.*x*, where *x* is a number.</span></span>  
  
  
