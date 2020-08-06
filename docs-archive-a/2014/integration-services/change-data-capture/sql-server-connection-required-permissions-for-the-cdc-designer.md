---
title: CDC デザイナーで使用する SQL Server 接続に必要な権限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 80334de2-17c1-43c9-951e-21a9f864e9cb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0815a5d8f1cb66dee0d290a45166ebb395c8efa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632037"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-designer"></a><span data-ttu-id="6eddd-102">CDC デザイナーで使用する SQL Server 接続に必要な権限</span><span class="sxs-lookup"><span data-stu-id="6eddd-102">SQL Server Connection Required Permissions for the CDC Designer</span></span>
  <span data-ttu-id="6eddd-103">CDC デザイナー コンソールのタスクを実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="6eddd-103">The CDC Designer Console requires connection information to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to perform its tasks.</span></span> <span data-ttu-id="6eddd-104">このトピックでは、 **との接続を設定するために** [SQL Server への接続] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ダイアログ ボックスで指定できる情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="6eddd-104">This topic describes the information that can be provided in the **Connect to SQL Server** dialog box for setting up the connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6eddd-105">**‭[SQL Server への接続]** ダイアログ ボックスは必要なときに開きます。たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続情報がない場合や、情報は存在しても接続に必要な権限がない場合などです。</span><span class="sxs-lookup"><span data-stu-id="6eddd-105">The **Connect to SQL Server** dialog box opens when necessary, such as when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection information is not available or when the information exists but the connection does not have the required permissions.</span></span>  
  
 <span data-ttu-id="6eddd-106">次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続が必要となる各種のタスクと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン/ユーザーに必要な権限について説明します。</span><span class="sxs-lookup"><span data-stu-id="6eddd-106">The following table describes the various tasks where a connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is required and the required permissions from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login/user.</span></span>  
  
|<span data-ttu-id="6eddd-107">タスク</span><span class="sxs-lookup"><span data-stu-id="6eddd-107">Task</span></span>|<span data-ttu-id="6eddd-108">最小限のアクセス許可</span><span class="sxs-lookup"><span data-stu-id="6eddd-108">Minimum Permissions</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="6eddd-109">関連する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを使用した CDC サービスおよびインスタンスの一覧表示</span><span class="sxs-lookup"><span data-stu-id="6eddd-109">View the list of CDC Services and Instances using the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>|<span data-ttu-id="6eddd-110">`db_datareader` ロール</span><span class="sxs-lookup"><span data-stu-id="6eddd-110">`db_datareader` role on MSXDBCDC</span></span>|  
|<span data-ttu-id="6eddd-111">CDC インスタンスの開始/停止</span><span class="sxs-lookup"><span data-stu-id="6eddd-111">Start/Stop CDC Instance(s)</span></span>|<span data-ttu-id="6eddd-112">`db_datareader` ロールと `db_datawriter` ロール</span><span class="sxs-lookup"><span data-stu-id="6eddd-112">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
|<span data-ttu-id="6eddd-113">CDC インスタンスの状態の表示</span><span class="sxs-lookup"><span data-stu-id="6eddd-113">View the CDC Instance status.</span></span>|<span data-ttu-id="6eddd-114">`db_owner` ロール</span><span class="sxs-lookup"><span data-stu-id="6eddd-114">`db_owner` role on the CDC Instance database</span></span>|  
|<span data-ttu-id="6eddd-115">新しい Oracle CDC インスタンス データベースの作成</span><span class="sxs-lookup"><span data-stu-id="6eddd-115">Create a new Oracle CDC Instance database.</span></span>|<span data-ttu-id="6eddd-116">`dbcreator` 固定サーバー ロール</span><span class="sxs-lookup"><span data-stu-id="6eddd-116">`dbcreator` fixed-server role</span></span>|  
|<span data-ttu-id="6eddd-117">新しい Oracle CDC インスタンスの作成</span><span class="sxs-lookup"><span data-stu-id="6eddd-117">Create a new Oracle CDC Instance.</span></span>|<span data-ttu-id="6eddd-118">`db_datareader` ロール</span><span class="sxs-lookup"><span data-stu-id="6eddd-118">`db_datareader` role on MSXDBCDC</span></span><br /><br /> <span data-ttu-id="6eddd-119">`db_owner` ロール</span><span class="sxs-lookup"><span data-stu-id="6eddd-119">`db_owner` role on the CDC database that was created.</span></span>|  
|<span data-ttu-id="6eddd-120">配置スクリプトの取得</span><span class="sxs-lookup"><span data-stu-id="6eddd-120">Get deployment scripts.</span></span>|<span data-ttu-id="6eddd-121">`db_datareader` ロールと `db_datawriter` ロール</span><span class="sxs-lookup"><span data-stu-id="6eddd-121">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span><br /><br /> <span data-ttu-id="6eddd-122">`db_owner` ロール</span><span class="sxs-lookup"><span data-stu-id="6eddd-122">`db_owner` role on the relatedCDC database</span></span>|  
|<span data-ttu-id="6eddd-123">構成の変更およびキャプチャ インスタンスの追加/削除</span><span class="sxs-lookup"><span data-stu-id="6eddd-123">Change configuration and add/remove capture instances.</span></span>|<span data-ttu-id="6eddd-124">`db_datareader` ロールと `db_datawriter` ロール</span><span class="sxs-lookup"><span data-stu-id="6eddd-124">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span><br /><br /> <span data-ttu-id="6eddd-125">`db_owner` ロール</span><span class="sxs-lookup"><span data-stu-id="6eddd-125">`db_owner` role on the related CDC database</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6eddd-126">参照</span><span class="sxs-lookup"><span data-stu-id="6eddd-126">See Also</span></span>  
 <span data-ttu-id="6eddd-127">[CDC デザイナー コンソールへのアクセス](access-the-cdc-designer-console.md) </span><span class="sxs-lookup"><span data-stu-id="6eddd-127">[Access the CDC Designer Console](access-the-cdc-designer-console.md) </span></span>  
 [<span data-ttu-id="6eddd-128">インスタンスの作成のための SQL Server 接続</span><span class="sxs-lookup"><span data-stu-id="6eddd-128">SQL Server Connection for Instance Creation</span></span>](sql-server-connection-for-instance-creation.md)  
  
  
