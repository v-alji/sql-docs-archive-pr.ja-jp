---
title: '[SQL Server エージェントのプロパティ] ([接続] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
author: stevestein
ms.author: sstein
ms.openlocfilehash: ec9ae575f1ced510d95256d6827435e5b6ad89d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644271"
---
# <a name="sql-server-agent-properties-connection-page"></a><span data-ttu-id="58a21-102">[SQL Server エージェントのプロパティ] ([接続] ページ)</span><span class="sxs-lookup"><span data-stu-id="58a21-102">SQL Server Agent Properties (Connection Page)</span></span>
  <span data-ttu-id="58a21-103">このページを使用すると、エージェントサービスからへの接続の設定を表示および変更 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] できます。</span><span class="sxs-lookup"><span data-stu-id="58a21-103">Use this page to view and modify the settings for the connection from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="58a21-104">Options</span><span class="sxs-lookup"><span data-stu-id="58a21-104">Options</span></span>  
 <span data-ttu-id="58a21-105">**[別名ローカル ホスト サーバー]**</span><span class="sxs-lookup"><span data-stu-id="58a21-105">**Alias local host server**</span></span>  
 <span data-ttu-id="58a21-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のローカル インスタンスへの接続に使用する別名を指定します。</span><span class="sxs-lookup"><span data-stu-id="58a21-106">Specifies the alias to use to connect to the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="58a21-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの既定の接続オプションを使用できない場合は、インスタンスの別名を定義し、ここでその別名を指定します。</span><span class="sxs-lookup"><span data-stu-id="58a21-107">If you cannot use the default connection options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, define an alias for the instance and specify the alias here.</span></span>  
  
 <span data-ttu-id="58a21-108">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="58a21-108">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="58a21-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続に使用する認証方法として設定します。</span><span class="sxs-lookup"><span data-stu-id="58a21-109">Sets [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication as the authentication method used to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58a21-110">エージェントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが実行に使用するアカウントとして接続します。</span><span class="sxs-lookup"><span data-stu-id="58a21-110">Agent connects as the account that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service runs as.</span></span>  
  
 <span data-ttu-id="58a21-111">**[SQL Server 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="58a21-111">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="58a21-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続に使用する認証方法として設定します。</span><span class="sxs-lookup"><span data-stu-id="58a21-112">Sets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication as the authentication method used to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58a21-113">認証は旧バージョンとの互換性を維持するために提供されます。</span><span class="sxs-lookup"><span data-stu-id="58a21-113">Authentication is provided for backward compatibility.</span></span> <span data-ttu-id="58a21-114">セキュリティを向上させるためには、可能な限り、Windows 認証を使用してください。</span><span class="sxs-lookup"><span data-stu-id="58a21-114">For improved security, use Windows Authentication if possible.</span></span>  
  
 <span data-ttu-id="58a21-115">**Login**</span><span class="sxs-lookup"><span data-stu-id="58a21-115">**Login**</span></span>  
 <span data-ttu-id="58a21-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]への接続に使用するログイン名を指定します。</span><span class="sxs-lookup"><span data-stu-id="58a21-116">Specifies the login name to use to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="58a21-117">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="58a21-117">**Password**</span></span>  
 <span data-ttu-id="58a21-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]への接続に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="58a21-118">Specifies the password to use to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
  
