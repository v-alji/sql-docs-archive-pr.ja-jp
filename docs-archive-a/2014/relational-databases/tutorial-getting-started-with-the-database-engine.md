---
title: 'チュートリアル : データベース エンジンの概要 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tutorials [connecting]
- tutorials [Database Engine]
- unable to connect [SQL Server]
- failure to connect [SQL Server]
- connecting tutorial [SQL Server]
ms.assetid: 655e709b-346b-469c-bddc-a5a0238d07e0
author: rothja
ms.author: jroth
ms.openlocfilehash: aaa1fb21c026d064c2b14db73aadc2b82e9c15d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644873"
---
# <a name="tutorial-getting-started-with-the-database-engine"></a><span data-ttu-id="4331d-102">チュートリアル : データベース エンジンの概要</span><span class="sxs-lookup"><span data-stu-id="4331d-102">Tutorial: Getting Started with the Database Engine</span></span>
  <span data-ttu-id="4331d-103">「 [!INCLUDE[ssDE](../includes/ssde-md.md)] の概要」チュートリアルへようこそ。</span><span class="sxs-lookup"><span data-stu-id="4331d-103">Welcome to the Getting Started with the [!INCLUDE[ssDE](../includes/ssde-md.md)] tutorial.</span></span> <span data-ttu-id="4331d-104">このチュートリアルは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を初めて使用するユーザーで、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] または [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]をインストールしたユーザーを対象にしています。</span><span class="sxs-lookup"><span data-stu-id="4331d-104">This tutorial is intended for users who are new to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and who have installed [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or [!INCLUDE[ssExpress](../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="4331d-105">この短いチュートリアルでは、 [!INCLUDE[ssDE](../includes/ssde-md.md)]の簡単な使用方法を学習できます。</span><span class="sxs-lookup"><span data-stu-id="4331d-105">This brief tutorial helps you get started using the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="4331d-106">学習する内容</span><span class="sxs-lookup"><span data-stu-id="4331d-106">What You Will Learn</span></span>  
 <span data-ttu-id="4331d-107">このチュートリアルでは、 [!INCLUDE[ssDE](../includes/ssde-md.md)] を使用して、ローカル コンピューターと別のコンピューターの両方から [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] に接続する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="4331d-107">This tutorial shows you how to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] on both the local computer and from another computer.</span></span>  
  
 <span data-ttu-id="4331d-108">このチュートリアルは、次の 2 つのレッスンで構成されています。</span><span class="sxs-lookup"><span data-stu-id="4331d-108">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="4331d-109">レッスン 1: データベース エンジンへの接続</span><span class="sxs-lookup"><span data-stu-id="4331d-109">Lesson 1: Connecting to the Database Engine</span></span>](lesson-1-connecting-to-the-database-engine.md)  
 <span data-ttu-id="4331d-110">このレッスンでは、 [!INCLUDE[ssDE](../includes/ssde-md.md)] に接続し、他のユーザーが接続できるようにする方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="4331d-110">In this lesson, you will learn how to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] and enable additional people to connect.</span></span>  
  
 [<span data-ttu-id="4331d-111">レッスン 2: 別のコンピューターからの接続</span><span class="sxs-lookup"><span data-stu-id="4331d-111">Lesson 2: Connecting from Another Computer</span></span>](lesson-2-connecting-from-another-computer.md)  
 <span data-ttu-id="4331d-112">このレッスンでは、別のコンピューターから [!INCLUDE[ssDE](../includes/ssde-md.md)] に接続する方法を学習します。これには、プロトコルを有効化する方法や、ポートやファイアウォール設定を構成する方法も含まれます。</span><span class="sxs-lookup"><span data-stu-id="4331d-112">In this lesson, you will learn how to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] from a second computer, including enabling protocols, configuring ports, and configuring firewall settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4331d-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="4331d-113">Requirements</span></span>  
 <span data-ttu-id="4331d-114">このチュートリアルに予備知識は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4331d-114">This tutorial has no knowledge prerequisites.</span></span>  
  
 <span data-ttu-id="4331d-115">このチュートリアルを使用するには、システムに以下のコンポーネントがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4331d-115">Your system must have the following installed to use this tutorial:</span></span>  
  
-   <span data-ttu-id="4331d-116">[https://login.microsoftonline.com/consumers/]([!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)])</span><span class="sxs-lookup"><span data-stu-id="4331d-116">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] <span data-ttu-id="4331d-117">は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] セットアップを実行してインストールできます。または、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/?LinkId=144346)からダウンロードしてインストールできます。</span><span class="sxs-lookup"><span data-stu-id="4331d-117">can be installed by running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] setup or by downloading and installing from [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=144346).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4331d-118">参照</span><span class="sxs-lookup"><span data-stu-id="4331d-118">See Also</span></span>  
 [<span data-ttu-id="4331d-119">チュートリアル: SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4331d-119">Tutorial: SQL Server Management Studio</span></span>](../ssms/tutorials/tutorial-sql-server-management-studio.md)  
  
  
