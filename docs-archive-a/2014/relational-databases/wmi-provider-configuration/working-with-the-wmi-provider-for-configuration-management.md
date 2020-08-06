---
title: WMI プロバイダーを使用した構成管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- WMI Provider for Configuration Management, connection strings
- WMI Provider for Configuration Management, security
- late binding [WMI]
- WMI Provider for Configuration Management, late binding
- binding [WMI]
ms.assetid: 34daa922-7074-41d0-9077-042bb18c222a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 80f311fb0abae2337f6ea4a5d5d85aaa0d320b94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640802"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a><span data-ttu-id="32f26-102">WMI Provider for Configuration Management の操作</span><span class="sxs-lookup"><span data-stu-id="32f26-102">Working with the WMI Provider for Configuration Management</span></span>
  <span data-ttu-id="32f26-103">WMI Provider for Computer Management を使用したプログラミングを行う前に、次の点について考慮してください。</span><span class="sxs-lookup"><span data-stu-id="32f26-103">Consider the following before programming with the WMI Provider for Computer Management:</span></span>  
  
## <a name="binding"></a><span data-ttu-id="32f26-104">バインド</span><span class="sxs-lookup"><span data-stu-id="32f26-104">Binding</span></span>  
 <span data-ttu-id="32f26-105"> WMI Provider for Configuration Management は、COM オブジェクト モデルであり、事前バインドも遅延バインドもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="32f26-105">The WMI Provider for Configuration Management is a COM object model and it supports early and late binding.</span></span> <span data-ttu-id="32f26-106">遅延バインドを行う場合、VBScript などのスクリプト言語を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス、ネットワーク設定、別名をプログラムで操作することができます。</span><span class="sxs-lookup"><span data-stu-id="32f26-106">With late binding you can use script languages, such as VBScript, to manipulate the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, network settings, and aliases programmatically.</span></span>  
  
 <span data-ttu-id="32f26-107">スクリプト言語を使用した WMI プロバイダー実装のプログラミングの詳細については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [Web サイト](https://go.microsoft.com/fwlink/?linkid=15426)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32f26-107">For further information about programming WMI Provider implementations using scripting languages, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [Web site](https://go.microsoft.com/fwlink/?linkid=15426).</span></span>  
  
## <a name="specifying-a-connection-string"></a><span data-ttu-id="32f26-108">接続文字列の指定</span><span class="sxs-lookup"><span data-stu-id="32f26-108">Specifying a Connection String</span></span>  
 <span data-ttu-id="32f26-109">アプリケーションは、プロバイダーによって定義された WMI 名前空間に接続することで、WMI Provider for Configuration Management を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="32f26-109">Applications direct the WMI Provider for Configuration Management to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by connecting to a WMI namespace defined by the provider.</span></span> <span data-ttu-id="32f26-110">Windows WMI サービスは、この名前空間をプロバイダー DLL にマップし、これをメモリに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="32f26-110">The Windows WMI service maps this namespace to the provider DLL and loads it into memory.</span></span> <span data-ttu-id="32f26-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスはすべて、1 つの WMI 名前空間で表されます。</span><span class="sxs-lookup"><span data-stu-id="32f26-111">All instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are represented with a single WMI namespace.</span></span> <span data-ttu-id="32f26-112">名前空間の既定値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="32f26-112">The namespace defaults to</span></span>  
  
```  
\\.\root\Microsoft\SqlServer\ComputerManagement12\instance_name  
```  
  
 <span data-ttu-id="32f26-113">`instance_name` の既定値は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインストール内の `MSSQLSERVER` になります。</span><span class="sxs-lookup"><span data-stu-id="32f26-113">where `instance_name` defaults to `MSSQLSERVER` in a default installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="32f26-114">**注:** Windows ファイアウォールを介して接続している場合は、コンピューターが適切に構成されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32f26-114">**Note:** If you are connecting through Windows Firewall you will need to make sure your computers are configured appropriately.</span></span> <span data-ttu-id="32f26-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)]MSDN [Web サイト](https://go.microsoft.com/fwlink/?linkid=15426)の Windows Management Instrumentation のドキュメントで、Windows ファイアウォール経由の接続に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32f26-115">See the "Connecting Through Windows Firewall" article in the Windows Management Instrumentation documentation on [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [Web site](https://go.microsoft.com/fwlink/?linkid=15426).</span></span>  
  
## <a name="permissions-and-server-authentication"></a><span data-ttu-id="32f26-116">権限とサーバー認証</span><span class="sxs-lookup"><span data-stu-id="32f26-116">Permissions and Server Authentication</span></span>  
 <span data-ttu-id="32f26-117">WMI Provider for Configuration Management にアクセスするには、クライアント WMI 管理スクリプトが、ターゲット コンピューター上の管理者のコンテキストで実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="32f26-117">To access the WMI Provider for Configuration Management, the client WMI management script must be running in the context of an administrator on the target computer.</span></span> <span data-ttu-id="32f26-118">アクセスするユーザーは、管理するコンピューターのローカル Windows 管理者グループのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="32f26-118">You need to be a member of the local Windows administrators group on the computer you want to manage.</span></span>  
  
 <span data-ttu-id="32f26-119">管理者は、グループ ポリシーを設定して、WMI プロバイダーへのユーザー アクセスを制御することができます。</span><span class="sxs-lookup"><span data-stu-id="32f26-119">The administrator can set group policies to control user access to WMI providers.</span></span> <span data-ttu-id="32f26-120">グループ ポリシーの設定の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーのヘルプの「グループ ポリシーと MMC」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32f26-120">For more information about setting group policies see "Group Policy and MMC" in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager Help.</span></span>  
  
 <span data-ttu-id="32f26-121">WMI 管理スクリプトを使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されるアカウントを更新することができます。</span><span class="sxs-lookup"><span data-stu-id="32f26-121">The WMI management script can be used to update the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services run.</span></span>  
  
 <span data-ttu-id="32f26-122">WMI Provider for Configuration Management では、セキュリティ証明書がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="32f26-122">Security certificates are supported by the WMI Provider for Configuration Management.</span></span> <span data-ttu-id="32f26-123">証明書の詳細については、「 [Encryption Hierarchy](../security/encryption/encryption-hierarchy.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32f26-123">For more information about certificates, see [Encryption Hierarchy](../security/encryption/encryption-hierarchy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32f26-124">参照</span><span class="sxs-lookup"><span data-stu-id="32f26-124">See Also</span></span>  
 [<span data-ttu-id="32f26-125">SQL Server 構成マネージャー</span><span class="sxs-lookup"><span data-stu-id="32f26-125">SQL Server Configuration Manager</span></span>](../sql-server-configuration-manager.md)  
  
  
