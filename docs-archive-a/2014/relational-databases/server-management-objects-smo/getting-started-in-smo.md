---
title: SMO | のはじめにMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, about SQL Server Management Objects
- SMO [SQL Server], about SQL Server Management Objects
ms.assetid: ecc62702-c0d5-4180-b3c2-16ec5030caa7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d90911932b5f9bfc91368e70e66d2b227a3964f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642729"
---
# <a name="getting-started-in-smo"></a><span data-ttu-id="91703-102">SMO の概要</span><span class="sxs-lookup"><span data-stu-id="91703-102">Getting Started in SMO</span></span>
  <span data-ttu-id="91703-103">このトピックでは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、管理オブジェクト (SMO) の使用を開始する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="91703-103">This topic contains information about getting started using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).</span></span> <span data-ttu-id="91703-104">SMO セクションは開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="91703-104">The SMO section is aimed at developers.</span></span> <span data-ttu-id="91703-105">次のリストは、SMO オブジェクト階層、SMO でプログラムを作成するための準備方法、異なるプログラミング言語で SMO プログラムを作成する方法、一般的および特定のプログラミング タスクについての情報の記載場所を知るために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="91703-105">The following list will help you to locate information about the SMO object hierarchy, how to prepare for writing programs in SMO, how to start writing an SMO program in different programming languages, and general and specific programming tasks.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="91703-106">**SMO の準備**</span><span class="sxs-lookup"><span data-stu-id="91703-106">**Preparing for SMO**</span></span><br /><br /> <span data-ttu-id="91703-107">-   [SMO の準備](../../database-engine/dev-guide/preparing-to-use-smo.md)については、sql-dmo とのシステム要件、インストール、および比較に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="91703-107">-   [Preparing for SMO](../../database-engine/dev-guide/preparing-to-use-smo.md) provides information about system requirements, installation, and comparisons with SQL-DMO.</span></span><br /><br /> <span data-ttu-id="91703-108">**オブジェクトモデル**</span><span class="sxs-lookup"><span data-stu-id="91703-108">**Object Model**</span></span><br /><br /> <span data-ttu-id="91703-109">-[オブジェクトモデル](smo-object-model.md)では、SMO オブジェクト階層と、オブジェクトが相互にどのように関連しているかが記述されています。</span><span class="sxs-lookup"><span data-stu-id="91703-109">-   The [Object Model](smo-object-model.md) describes the SMO object hierarchy and how the objects relate to one another.</span></span><br /><br /> <span data-ttu-id="91703-110">**プログラミング言語**</span><span class="sxs-lookup"><span data-stu-id="91703-110">**Programming Languages**</span></span><br /><br /> <span data-ttu-id="91703-111">-   [プログラミング言語](smo-programming-languages.md)プログラミング環境について説明し、C# および VISUAL BASIC で SMO プログラムの記述を開始するための詳細な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="91703-111">-   [Programming Languages](smo-programming-languages.md) describes the programming environment and includes detailed procedures to start writing an SMO program in C# and Visual Basic.</span></span>|<span data-ttu-id="91703-112">**SMO での一般的なプログラミング**</span><span class="sxs-lookup"><span data-stu-id="91703-112">**General Programming in SMO**</span></span><br /><br /> <span data-ttu-id="91703-113">-   [Smo での一般的なプログラミング](create-program/creating-smo-programs.md)は、smo を使用したプログラミングの概要です。</span><span class="sxs-lookup"><span data-stu-id="91703-113">-   [General Programming in SMO](create-program/creating-smo-programs.md) is an introduction to programming with SMO.</span></span> <span data-ttu-id="91703-114">このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する方法、およびプロパティ、メソッド、コレクションを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="91703-114">This topic describes how to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and how to use properties, methods, and collections.</span></span> <span data-ttu-id="91703-115">より高度なトピックでは、データ型、トランザクション、キャプチャ モードの設定、イベントと例外の処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="91703-115">More advanced topics describe data types, transactions, setting the capture mode, and event and exception handling.</span></span><br /><br /> <span data-ttu-id="91703-116">**プログラミング特有のタスク**</span><span class="sxs-lookup"><span data-stu-id="91703-116">**Programming Specific Tasks**</span></span><br /><br /> <span data-ttu-id="91703-117">-特定のタスクのプログラミングに関するセクションには、SMO を使用して特定のタスクを[プログラミング](tasks/programming-specific-tasks.md)する方法に関する概念と手順が記載されています。</span><span class="sxs-lookup"><span data-stu-id="91703-117">-   The [Programming Specific Tasks](tasks/programming-specific-tasks.md) section contains concepts and procedures about how to program specific tasks by using SMO.</span></span> <span data-ttu-id="91703-118">また、このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の完全なプログラムによる管理についても説明しています。</span><span class="sxs-lookup"><span data-stu-id="91703-118">The topic also describes complete programmatic management of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
  
