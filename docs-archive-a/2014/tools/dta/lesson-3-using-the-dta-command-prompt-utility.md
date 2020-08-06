---
title: 'レッスン 3: dta コマンドプロンプトユーティリティの使用 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: 30f27f4d-8852-4b12-ba62-57f63e496f1d
author: stevestein
ms.author: sstein
ms.openlocfilehash: abbde02cd73e01937e6d0669c10f2db28da8a76e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711321"
---
# <a name="lesson-3-using-the-dta-command-prompt-utility"></a><span data-ttu-id="0f5d4-102">レッスン 3 : dta コマンド プロンプト ユーティリティの使用</span><span class="sxs-lookup"><span data-stu-id="0f5d4-102">Lesson 3: Using the dta Command Prompt Utility</span></span>
  <span data-ttu-id="0f5d4-103">**dta** コマンド プロンプト ユーティリティは、データベース エンジン チューニング アドバイザーの機能以外にも機能があります。</span><span class="sxs-lookup"><span data-stu-id="0f5d4-103">The **dta** command-prompt utility offers functionality in addition to that provided by the Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="0f5d4-104">データベース エンジン チューニング アドバイザーの XML スキーマを使用すれば、使い慣れた XML ツールで、このユーティリティへの入力ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0f5d4-104">You can use your favorite XML tools to create input files for the utility by using the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="0f5d4-105">このスキーマは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール時にインストールされ、C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd に格納されます。</span><span class="sxs-lookup"><span data-stu-id="0f5d4-105">This schema is installed when you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and can be found at: C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd.</span></span>  
  
 <span data-ttu-id="0f5d4-106">データベース エンジン チューニング アドバイザーの XML スキーマは、 [Microsoft Web サイト](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)から入手することもできます。</span><span class="sxs-lookup"><span data-stu-id="0f5d4-106">The Database Engine Tuning Advisor XML schema is also available online at [this Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409).</span></span>  
  
 <span data-ttu-id="0f5d4-107">この XML スキーマにより、チューニング オプションをより柔軟に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="0f5d4-107">The Database Engine Tuning Advisor XML schema provides more flexibility to set tuning options.</span></span> <span data-ttu-id="0f5d4-108">たとえば、"what-if" 分析を実行できます。</span><span class="sxs-lookup"><span data-stu-id="0f5d4-108">For example, it enables you to perform "what-if" analysis.</span></span> <span data-ttu-id="0f5d4-109">"what-if" 分析とは、チューニングするデータベースに対して実在の物理設計構造と仮想の物理設計構造のセットを指定し、それをデータベース エンジン チューニング アドバイザーで分析する手法です。これにより、仮想的な物理設計がクエリ処理のパフォーマンスを向上させるかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="0f5d4-109">"What-if" analysis involves specifying a set of existing and hypothetical physical design structures for the database you want to tune, and then analyzing it with the Database Engine Tuning Advisor to find out whether this hypothetical physical design will improve query processing performance.</span></span> <span data-ttu-id="0f5d4-110">このタイプの分析には、実際に実装しなくても新しい構成を評価できるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="0f5d4-110">This type of analysis provides the advantage of evaluating the new configuration without incurring the overhead of actually implementing it.</span></span> <span data-ttu-id="0f5d4-111">仮想的な物理構造により十分にパフォーマンスが向上しなくとも、十分な結果が得られる構成になるまで再び構造を変えて分析するのは容易です。</span><span class="sxs-lookup"><span data-stu-id="0f5d4-111">If your hypothetical physical design does not provide the performance improvements you want, it is easy to change it and analyze it again until you reach the configuration that produces the results you need.</span></span>  
  
 <span data-ttu-id="0f5d4-112">また、データベース エンジン チューニング アドバイザーの XML スキーマと **dta** コマンド プロンプト ユーティリティを使用すると、データベース エンジン チューニング アドバイザーの機能をスクリプトに組み込み、そのスクリプトを他のデータベース設計ツールで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0f5d4-112">In addition, using the Database Engine Tuning Advisor XML schema and the **dta** command-prompt utility, you can incorporate Database Engine Tuning Advisor functionality into scripts and use it with other database design tools.</span></span>  
  
 <span data-ttu-id="0f5d4-113">データベース エンジン チューニング アドバイザーの XML 入力機能の使用方法は、このレッスンでは扱いません。</span><span class="sxs-lookup"><span data-stu-id="0f5d4-113">Using the XML input functionality of Database Engine Tuning Advisor is beyond the scope of this lesson.</span></span>  
  
 <span data-ttu-id="0f5d4-114">このレッスンでは、 **dta** コマンド プロンプト ユーティリティの基本的な構文を紹介するほか、ヘルプへのアクセス方法を説明し、簡単なワークロードをチューニングします。</span><span class="sxs-lookup"><span data-stu-id="0f5d4-114">This lesson provides an introduction to the basic **dta** command-prompt utility syntax, how to access help, and practice for tuning simple workloads.</span></span>  
  
 <span data-ttu-id="0f5d4-115">ここで説明する内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0f5d4-115">It contains the following topic:</span></span>  
  
-   <span data-ttu-id="0f5d4-116">**Dta**コマンドプロンプトユーティリティの起動とワークロードのチューニング</span><span class="sxs-lookup"><span data-stu-id="0f5d4-116">Starting the **dta** Command Prompt Utility and Tuning a Workload</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="0f5d4-117">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="0f5d4-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="0f5d4-118">dta コマンド プロンプト ユーティリティの起動とワークロードのチューニング</span><span class="sxs-lookup"><span data-stu-id="0f5d4-118">Starting the dta Command Prompt Utility and Tuning a Workload</span></span>](lesson-1-1-tuning-a-workload.md)  
  
  
