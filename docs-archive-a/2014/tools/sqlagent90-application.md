---
title: sqlagent90 Application |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- starting SQL Server Agent
- sqlagent90 application
- SQL Server Agent, starting
- command prompt utilities [SQL Server], sqlagent90
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
author: stevestein
ms.author: sstein
ms.openlocfilehash: 290cb69f39aa3b08bb290c210b2d37977614a1ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634182"
---
# <a name="sqlagent90-application"></a><span data-ttu-id="7254e-102">sqlagent90 アプリケーション</span><span class="sxs-lookup"><span data-stu-id="7254e-102">sqlagent90 Application</span></span>
  <span data-ttu-id="7254e-103">**sqlagent90** アプリケーションは、コマンド プロンプトから [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを起動します。</span><span class="sxs-lookup"><span data-stu-id="7254e-103">The **sqlagent90** application starts [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent from the command prompt.</span></span> <span data-ttu-id="7254e-104">通常、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントは [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] から実行するか、またはアプリケーションで SQL-SMO メソッドを使って実行します。</span><span class="sxs-lookup"><span data-stu-id="7254e-104">Usually, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should be run from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or by using SQL-SMO methods in an application.</span></span> <span data-ttu-id="7254e-105">ただし、 **エージェントを診断する場合や、プライマリ サポート プロバイダーから指示された場合は、コマンド プロンプトから** sqlagent90 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を実行してください。</span><span class="sxs-lookup"><span data-stu-id="7254e-105">Only run **sqlagent90** from the command prompt when you are diagnosing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent, or when you are directed to it by your primary support provider.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7254e-106">構文</span><span class="sxs-lookup"><span data-stu-id="7254e-106">Syntax</span></span>  
  
```  
  
sqlagent90  
-c [-v] [-iinstance_name]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7254e-107">引数</span><span class="sxs-lookup"><span data-stu-id="7254e-107">Arguments</span></span>  
 <span data-ttu-id="7254e-108">**-c**</span><span class="sxs-lookup"><span data-stu-id="7254e-108">**-c**</span></span>  
 <span data-ttu-id="7254e-109">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントをコマンド プロンプトから実行し、Microsoft Windows サービス コントロール マネージャーの制御下にないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="7254e-109">Indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent is running from the command prompt and is independent of the Microsoft Windows Services Control Manager.</span></span> <span data-ttu-id="7254e-110">**-c** を使用する場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを、管理ツールのサービス アプリケーションまたは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーから制御することはできません。</span><span class="sxs-lookup"><span data-stu-id="7254e-110">When **-c** is used, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent cannot be controlled from either the Services application in Administrative Tools or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="7254e-111">この引数は必須です。</span><span class="sxs-lookup"><span data-stu-id="7254e-111">This argument is mandatory.</span></span>  
  
 <span data-ttu-id="7254e-112">**-v**</span><span class="sxs-lookup"><span data-stu-id="7254e-112">**-v**</span></span>  
 <span data-ttu-id="7254e-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを冗長モードで実行し、診断情報をコマンド プロンプト ウィンドウに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="7254e-113">Indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent runs in verbose mode and writes diagnostic information to the command-prompt window.</span></span> <span data-ttu-id="7254e-114">診断情報は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントのエラー ログに書き込まれる情報と同じです。</span><span class="sxs-lookup"><span data-stu-id="7254e-114">The diagnostic information is the same as the information written to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent error log.</span></span>  
  
 <span data-ttu-id="7254e-115">**-i** *instance_name*</span><span class="sxs-lookup"><span data-stu-id="7254e-115">**-i** *instance_name*</span></span>  
 <span data-ttu-id="7254e-116">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance_name *によって指定された名前付き*インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="7254e-116">Indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent connects to the named [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance specified by *instance_name*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7254e-117">解説</span><span class="sxs-lookup"><span data-stu-id="7254e-117">Remarks</span></span>  
 <span data-ttu-id="7254e-118">**sqlagent90** は、 **-v** スイッチが指定された場合にのみ、著作権に関するメッセージを表示した後にコマンド プロンプト ウィンドウに出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="7254e-118">After displaying a copyright message, **sqlagent90** displays output in the command prompt window only when the **-v** switch is specified.</span></span> <span data-ttu-id="7254e-119">**sqlagent90**を停止するには、コマンド プロンプトで Ctrl キーを押しながら C キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7254e-119">To stop **sqlagent90**, press CTRL+C at the command prompt.</span></span> <span data-ttu-id="7254e-120">**sqlagent90**を停止する前に、コマンド プロンプト ウィンドウを閉じないでください。</span><span class="sxs-lookup"><span data-stu-id="7254e-120">Do not close the command-prompt window before stopping **sqlagent90**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7254e-121">参照</span><span class="sxs-lookup"><span data-stu-id="7254e-121">See Also</span></span>  
 [<span data-ttu-id="7254e-122">管理タスクの自動化 &#40;SQL Server エージェント&#41;</span><span class="sxs-lookup"><span data-stu-id="7254e-122">Automated Administration Tasks &#40;SQL Server Agent&#41;</span></span>](../ssms/agent/automated-administration-tasks-sql-server-agent.md)  
  
  
