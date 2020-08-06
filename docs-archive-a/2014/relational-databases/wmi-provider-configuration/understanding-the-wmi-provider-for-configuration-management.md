---
title: WMI Provider for Configuration Management についてMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0f4f38265093fdb0c27d6bd49ff64ba4b572111e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630818"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a><span data-ttu-id="f849e-102">WMI Provider for Configuration Management について</span><span class="sxs-lookup"><span data-stu-id="f849e-102">Understanding the WMI Provider for Configuration Management</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="f849e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]には、構成管理用の WMI プロバイダーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f849e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the WMI Provider for Configuration Management.</span></span> <span data-ttu-id="f849e-104">これにより、WMI (Windows Management Instrumentation) を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のクライアントおよびサーバーのネットワーク設定、およびサーバー別名を管理することができます。</span><span class="sxs-lookup"><span data-stu-id="f849e-104">This lets you use Windows Management Instrumentation (WMI) to manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client and server network settings, and server aliases.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="f849e-105">サービス、ネットワーク設定、およびエイリアスは、コンピューターの root\Microsoft\SqlServer\ComputerManagement*nn*名前空間の WMI オブジェクトによって表されます。</span><span class="sxs-lookup"><span data-stu-id="f849e-105">services, network settings, and aliases are represented by WMI objects in the root\Microsoft\SqlServer\ComputerManagement*nn* namespace of the computer.</span></span> <span data-ttu-id="f849e-106">指定されたコンピューター上で WMI プロバイダーを使用して接続が確立された後、サービス、ネットワーク設定、別名は、WQL またはスクリプティング言語を使用してクエリを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f849e-106">After a connection is established with the WMI provider on the specified computer, the services, network settings, and aliases can be queried using WQL or a scripting language.</span></span>  
  
 <span data-ttu-id="f849e-107">WMI プロバイダーは、インスタンス プロバイダーです。</span><span class="sxs-lookup"><span data-stu-id="f849e-107">The WMI Provider is an instance provider.</span></span> <span data-ttu-id="f849e-108">[WMI クラス](../wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md)のインスタンスを提供し、次の非同期操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="f849e-108">It supplies instances of the [WMI Classes](../wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) and supports the following asynchronous operations.</span></span>  
  
 <span data-ttu-id="f849e-109">インスタンスの取得</span><span class="sxs-lookup"><span data-stu-id="f849e-109">Instance retrieval</span></span>  
 <span data-ttu-id="f849e-110">特定のクラス型インスタンスの取得です。</span><span class="sxs-lookup"><span data-stu-id="f849e-110">Retrieval of a particular class type instance.</span></span>  
  
 <span data-ttu-id="f849e-111">列挙</span><span class="sxs-lookup"><span data-stu-id="f849e-111">Enumeration</span></span>  
 <span data-ttu-id="f849e-112">クラス型のすべてのインスタンスの列挙です。</span><span class="sxs-lookup"><span data-stu-id="f849e-112">Enumeration of all instances of a class type.</span></span>  
  
 <span data-ttu-id="f849e-113">変更</span><span class="sxs-lookup"><span data-stu-id="f849e-113">Modification</span></span>  
 <span data-ttu-id="f849e-114">クラス型の特定のインスタンスの変更です。</span><span class="sxs-lookup"><span data-stu-id="f849e-114">Modification of a particular instance of a class type.</span></span>  
  
 <span data-ttu-id="f849e-115">クラスには、クラスのプロパティの変更を許可するメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="f849e-115">Classes have methods that allow the modification of their properties.</span></span>  
  
 <span data-ttu-id="f849e-116">削除</span><span class="sxs-lookup"><span data-stu-id="f849e-116">Deletion</span></span>  
 <span data-ttu-id="f849e-117">クラス型の特定のインスタンスの削除です。</span><span class="sxs-lookup"><span data-stu-id="f849e-117">Removing a particular instance of a class type.</span></span>  
  
 <span data-ttu-id="f849e-118">クエリ処理</span><span class="sxs-lookup"><span data-stu-id="f849e-118">Query processing</span></span>  
 <span data-ttu-id="f849e-119">フィルターに基づいたクラス型のインスタンスの列挙です。</span><span class="sxs-lookup"><span data-stu-id="f849e-119">Enumeration of instances of a class type based on a filter.</span></span>  
  
 <span data-ttu-id="f849e-120">構成管理用の WMI プロバイダーを使用した管理アプリケーションの例については、「 [Wmi provider For Configuration management での WQL およびスクリプト言語の使用](using-wql-and-scripting-languages-with-the-wmi-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f849e-120">For examples of management application using the WMI Provider for Configuration Management, see [Using WQL and Scripting Languages with the WMI Provider for Configuration Management](using-wql-and-scripting-languages-with-the-wmi-provider.md).</span></span>  
  
 <span data-ttu-id="f849e-121">WMI プロバイダーを使用した管理アプリケーションのプログラミングの詳細については、.NET Framework SDK の WMI のドキュメントを参照してください [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f849e-121">For more information about programming management applications using the WMI Provider, see the WMI documentation in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework SDK.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f849e-122">参照</span><span class="sxs-lookup"><span data-stu-id="f849e-122">See Also</span></span>  
 <span data-ttu-id="f849e-123">[WMI Provider for Configuration Management の使用](working-with-the-wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="f849e-123">[Working with the WMI Provider for Configuration Management](working-with-the-wmi-provider-for-configuration-management.md) </span></span>  
 [<span data-ttu-id="f849e-124">WQL およびスクリプティング言語での WMI Provider for Configuration Management の使用</span><span class="sxs-lookup"><span data-stu-id="f849e-124">Using WQL and Scripting Languages with the WMI Provider for Configuration Management</span></span>](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
