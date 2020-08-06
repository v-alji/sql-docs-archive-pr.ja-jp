---
title: ユーザー辞書によるワード ブレーカーの動作のカスタマイズ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9fb02a47da20134925d9b2486ea0c08091af4aa6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716213"
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a><span data-ttu-id="7159b-102">ユーザー辞書によるワード ブレーカーの動作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="7159b-102">Customize the Behavior of Word Breakers with a Custom Dictionary</span></span>
  <span data-ttu-id="7159b-103">言語固有のユーザー辞書ファイルを作成することで、特定の言語のワード ブレーカーの動作をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="7159b-103">You can customize the behavior of the word breaker for a particular language by creating a language-specific custom dictionary file.</span></span> <span data-ttu-id="7159b-104">たとえば、特定の用語やパターンがワード ブレーカーによって区切られないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="7159b-104">For example, you can prevent the word breaker from breaking certain terms or patterns.</span></span>  
  
 <span data-ttu-id="7159b-105">詳細については、次の SharePoint の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7159b-105">For more information, see the following SharePoint article:</span></span>  
  
 [<span data-ttu-id="7159b-106">ユーザー辞書を作成する (SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="7159b-106">Create a custom dictionary (SharePoint Server 2010)</span></span>](https://go.microsoft.com/fwlink/?LinkId=215011)  
  
 <span data-ttu-id="7159b-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、ユーザー辞書ファイルを次のフォルダーに配置します。</span><span class="sxs-lookup"><span data-stu-id="7159b-107">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], place custom dictionary files in the following folder:</span></span>  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 <span data-ttu-id="7159b-108">ユーザー辞書ファイルの作成または変更後、次のコマンドで SQL フルテキスト デーモン ランチャーを再起動します。</span><span class="sxs-lookup"><span data-stu-id="7159b-108">After creating or changing custom dictionary files, restart the SQL Full-text Daemon Launcher with the following command:</span></span>  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
