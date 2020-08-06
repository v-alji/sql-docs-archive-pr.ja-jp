---
title: CDC Service で使用する SQL Server 接続に必要な権限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e63b98ffd0371bd5b70ecc0ac843ad40a4a5d03e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639598"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-service"></a><span data-ttu-id="02c1e-102">CDC Service で使用する SQL Server 接続に必要な権限</span><span class="sxs-lookup"><span data-stu-id="02c1e-102">SQL Server Connection Required Permissions for the CDC Service</span></span>
  <span data-ttu-id="02c1e-103">CDC Service 構成コンソールのタスクを実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="02c1e-103">The CDC Service Configuration Console requires connection information to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to perform their tasks.</span></span> <span data-ttu-id="02c1e-104">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]との接続を設定するために [SQL Server への接続] ダイアログ ボックスで指定できる情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="02c1e-104">This topic describes the information that can be provided in the Connect to SQL Server dialog box for setting up the connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="02c1e-105">‭[SQL Server への接続] ダイアログ ボックスは必要なときに開きます。たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続情報がない場合や、情報は存在しても接続に必要な権限がない場合などです。</span><span class="sxs-lookup"><span data-stu-id="02c1e-105">The Connect to SQL Server dialog box opens when necessary, such as when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection information is not available or when the information exists but the connection does not have the required permissions.</span></span>  
  
 <span data-ttu-id="02c1e-106">次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続が必要となる各種のタスクと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン/ユーザーに必要な権限について説明します。</span><span class="sxs-lookup"><span data-stu-id="02c1e-106">The following table describes the various tasks where a connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is required and the required permissions from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login/user.</span></span>  
  
|<span data-ttu-id="02c1e-107">タスク</span><span class="sxs-lookup"><span data-stu-id="02c1e-107">Task</span></span>|<span data-ttu-id="02c1e-108">最小限のアクセス許可</span><span class="sxs-lookup"><span data-stu-id="02c1e-108">Minimum Permissions</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="02c1e-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを準備する。</span><span class="sxs-lookup"><span data-stu-id="02c1e-109">Prepare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instance.</span></span>|<span data-ttu-id="02c1e-110">`dbcreator` 固定サーバー ロール</span><span class="sxs-lookup"><span data-stu-id="02c1e-110">`dbcreator` fixed-server role</span></span>|  
|<span data-ttu-id="02c1e-111">Oracle CDC サービスが使用する Oracle CDC Service-SQLServer ログインを作成する。</span><span class="sxs-lookup"><span data-stu-id="02c1e-111">Create an Oracle CDC Service-SQL Server login for use by the Oracle CDC service.</span></span>|<span data-ttu-id="02c1e-112">`public` 固定サーバー ロール</span><span class="sxs-lookup"><span data-stu-id="02c1e-112">`public` fixed-server role</span></span>|  
|<span data-ttu-id="02c1e-113">MSXDBCDC に新しいサービスを登録するために使用する Oracle CDC Service ログインを作成する。</span><span class="sxs-lookup"><span data-stu-id="02c1e-113">Create an Oracle CDC Service-login to use for registering the new service in MSXDBCDC.</span></span>|<span data-ttu-id="02c1e-114">`db_datareader` ロールと `db_datawriter` ロール</span><span class="sxs-lookup"><span data-stu-id="02c1e-114">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
|<span data-ttu-id="02c1e-115">MSXDBCDC のサービスの登録を更新するために使用する Oracle CDC Service ログインを編集する。</span><span class="sxs-lookup"><span data-stu-id="02c1e-115">Edit an Oracle CDC Service-login to use for updating the registration of the service in MSXDBCDC.</span></span>|<span data-ttu-id="02c1e-116">`db_datareader` ロールと `db_datawriter` ロール</span><span class="sxs-lookup"><span data-stu-id="02c1e-116">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
|<span data-ttu-id="02c1e-117">MSXDBCDC のサービスの登録を更新するために使用する Oracle CDC Service ログインを削除する。</span><span class="sxs-lookup"><span data-stu-id="02c1e-117">Delete an Oracle CDC Service-login to use for updating the registration of the service in MSXDBCDC.</span></span>|<span data-ttu-id="02c1e-118">`db_datareader` ロールと `db_datawriter` ロール</span><span class="sxs-lookup"><span data-stu-id="02c1e-118">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02c1e-119">参照</span><span class="sxs-lookup"><span data-stu-id="02c1e-119">See Also</span></span>  
 <span data-ttu-id="02c1e-120">[SQL Server への接続](connection-to-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="02c1e-120">[Connection to SQL Server](connection-to-sql-server.md) </span></span>  
 [<span data-ttu-id="02c1e-121">削除用の SQLServer への接続</span><span class="sxs-lookup"><span data-stu-id="02c1e-121">Connection to SQL Server for Delete</span></span>](connection-to-sql-server-for-delete.md)  
  
  
