---
title: SMO 接続マネージャーエディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.smoconnection.f1
helpviewer_keywords:
- SMO Connection Manager Editor
ms.assetid: bed52d80-ed2a-4bf4-bf7c-481b6e228ca4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6b3d1ccea1a3a4e963c6b6f8c7dbd58a374b3de4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742354"
---
# <a name="smo-connection-manager-editor"></a><span data-ttu-id="510f8-102">SMO 接続マネージャー エディター</span><span class="sxs-lookup"><span data-stu-id="510f8-102">SMO Connection Manager Editor</span></span>
  <span data-ttu-id="510f8-103">**[SMO 接続マネージャー エディター]** を使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトを転送するさまざまなタスクで使用される [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 接続を構成します。</span><span class="sxs-lookup"><span data-stu-id="510f8-103">Use the **SMO Connection Manager Editor** to configure a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] connection for use by the various tasks that transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
 <span data-ttu-id="510f8-104">SMO 接続マネージャーの詳細については、「 [SMO Connection Manager](connection-manager/smo-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="510f8-104">To learn more about the SMO connection manager, see [SMO Connection Manager](connection-manager/smo-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="510f8-105">Options</span><span class="sxs-lookup"><span data-stu-id="510f8-105">Options</span></span>  
 <span data-ttu-id="510f8-106">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="510f8-106">**Server name**</span></span>  
 <span data-ttu-id="510f8-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの名前を入力するか、サーバーを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="510f8-107">Type the name of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance or select the server name from the list.</span></span>  
  
 <span data-ttu-id="510f8-108">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="510f8-108">**Refresh**</span></span>  
 <span data-ttu-id="510f8-109">ネットワークで検出できる利用可能な [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの一覧を更新します。</span><span class="sxs-lookup"><span data-stu-id="510f8-109">Refresh the list of available [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances that can be detected on the network.</span></span>  
  
 <span data-ttu-id="510f8-110">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="510f8-110">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="510f8-111">Windows 認証を使用して、選択されている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="510f8-111">Use Windows Authentication to connect to the selected [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="510f8-112">**[SQL Server 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="510f8-112">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="510f8-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用して、選択されている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="510f8-113">Use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the selected [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="510f8-114">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="510f8-114">**User name**</span></span>  
 <span data-ttu-id="510f8-115">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を選択している場合は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="510f8-115">If you have selected [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] authentication, enter the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] user name.</span></span>  
  
 <span data-ttu-id="510f8-116">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="510f8-116">**Password**</span></span>  
 <span data-ttu-id="510f8-117">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を選択している場合は、パスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="510f8-117">If you have selected [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] authentication, enter the password.</span></span>  
  
 <span data-ttu-id="510f8-118">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="510f8-118">**Test Connection**</span></span>  
 <span data-ttu-id="510f8-119">構成されたとおりに接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="510f8-119">Test the connection as configured.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="510f8-120">参照</span><span class="sxs-lookup"><span data-stu-id="510f8-120">See Also</span></span>  
 [<span data-ttu-id="510f8-121">Integration Services のエラーおよびメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="510f8-121">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
