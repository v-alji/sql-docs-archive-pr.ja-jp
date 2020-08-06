---
title: 中央管理サーバーを使用した複数のサーバーの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- central management server
- multiserver administration [SQL Server]
- master servers [SQL Server], central management servers
- target configuration [SQL Server]
- server configuration [SQL Server]
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3906165b595f6faa15812f70377a3bc0f550e52e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715446"
---
# <a name="administer-multiple-servers-using-central-management-servers"></a><span data-ttu-id="fd992-102">中央管理サーバーを使用した複数のサーバーの管理</span><span class="sxs-lookup"><span data-stu-id="fd992-102">Administer Multiple Servers Using Central Management Servers</span></span>
  <span data-ttu-id="fd992-103">中央管理サーバーを指定し、サーバー グループを作成することで、複数のサーバーを管理できます。</span><span class="sxs-lookup"><span data-stu-id="fd992-103">You can administer multiple servers by designating Central Management Servers and creating server groups.</span></span>  
  
## <a name="benefits-of-central-management-servers-and-server-groups"></a><span data-ttu-id="fd992-104">中央管理サーバーとサーバー グループの利点</span><span class="sxs-lookup"><span data-stu-id="fd992-104">Benefits of Central Management Servers and Server Groups</span></span>  
 <span data-ttu-id="fd992-105">中央管理サーバーとして指定した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスによってサーバー グループが管理され、サーバー グループによって [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 1 つ以上のインスタンスの接続情報が管理されます。</span><span class="sxs-lookup"><span data-stu-id="fd992-105">An instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that is designated as a Central Management Server maintains server groups that contain the connection information for one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fd992-106">サーバー グループに対しては、[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントおよびポリシー ベースの管理ポリシーを同時に実行できます。</span><span class="sxs-lookup"><span data-stu-id="fd992-106">[!INCLUDE[tsql](../includes/tsql-md.md)] statements and Policy-Based Management policies can be executed at the same time against server groups.</span></span> <span data-ttu-id="fd992-107">中央管理サーバーを通じて管理されているインスタンスの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログ ファイルを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="fd992-107">You can also view the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] log files on instances that are managed through a Central Management Server.</span></span> <span data-ttu-id="fd992-108">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] では、中央管理サーバーを指定できません。</span><span class="sxs-lookup"><span data-stu-id="fd992-108">Versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] cannot be designated as a Central Management Server.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="fd992-109">ステートメントは、登録済みサーバー内のローカル サーバー グループに対しても実行できます。</span><span class="sxs-lookup"><span data-stu-id="fd992-109">statements can also be executed against local server groups in Registered Servers.</span></span>  
  
### <a name="related-tasks"></a><span data-ttu-id="fd992-110">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="fd992-110">Related Tasks</span></span>  
 <span data-ttu-id="fd992-111">中央管理サーバーとサーバー グループを作成するには、 **の** [登録済みサーバー] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ウィンドウを使用します。</span><span class="sxs-lookup"><span data-stu-id="fd992-111">To create a Central Management Server and server groups, use the **Registered Servers** window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="fd992-112">中央管理サーバーを、それ自体が管理するグループのメンバーにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="fd992-112">Note that the Central Management Server cannot be a member of a group that it maintains.</span></span> <span data-ttu-id="fd992-113">中央管理サーバーとサーバー グループの作成方法については、「[中央管理サーバーおよびサーバー グループの作成 &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd992-113">For more information about how to create Central Management Servers and server groups, see [Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd992-114">参照</span><span class="sxs-lookup"><span data-stu-id="fd992-114">See Also</span></span>  
 [<span data-ttu-id="fd992-115">ポリシー ベースの管理を使用したサーバーの管理</span><span class="sxs-lookup"><span data-stu-id="fd992-115">Administer Servers by Using Policy-Based Management</span></span>](policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
