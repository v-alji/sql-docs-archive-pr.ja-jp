---
title: その他のファイル | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio], miscellaneous
- projects [SQL Server Management Studio], files
- solutions [SQL Server Management Studio], files
- miscellaneous files folder [SQL Server]
ms.assetid: 3c952b0b-8f5f-4d86-9e5d-616c10b9df0d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f65c04326e791fa3684a06213c3042a42f2f2ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717157"
---
# <a name="miscellaneous-files"></a><span data-ttu-id="7df7a-102">その他のファイル</span><span class="sxs-lookup"><span data-stu-id="7df7a-102">Miscellaneous Files</span></span>
  <span data-ttu-id="7df7a-103">プロジェクトの外部のファイルのことを "*その他のファイル*" といいます。</span><span class="sxs-lookup"><span data-stu-id="7df7a-103">Files that are external to any project are called *miscellaneous files*.</span></span> <span data-ttu-id="7df7a-104">ソリューションを開いているときには、プロジェクトに関連するその他のファイルを開いて修正できます。</span><span class="sxs-lookup"><span data-stu-id="7df7a-104">When you have a solution open, you can open and modify miscellaneous files related to the project.</span></span> <span data-ttu-id="7df7a-105">その他のファイルとして分類されるのは、プロジェクトのコード エディターにファイル拡張子が関連付けられていないファイルです。</span><span class="sxs-lookup"><span data-stu-id="7df7a-105">A file is classified as a miscellaneous file if the file extension is not associated with the project code editor.</span></span> <span data-ttu-id="7df7a-106">たとえば、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプト プロジェクトの場合、拡張子が .txt や .mdx のファイルはその他のファイルとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="7df7a-106">For example, in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Scripts Project, files with the extension .txt or .mdx will be treated as miscellaneous files.</span></span> <span data-ttu-id="7df7a-107">MDX プロジェクトでは、拡張子が .txt や .sql のファイルはその他のファイルとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="7df7a-107">In an MDX project, files with the extension of .txt or .sql will be treated as miscellaneous files.</span></span> <span data-ttu-id="7df7a-108">ファイル拡張子をコードエディターに関連付ける方法については、「[ファイル拡張子をコードエディターに関連付ける](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7df7a-108">To associate a file extension with a code editor, see [Associate File Extensions to a Code Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).</span></span>  
  
 <span data-ttu-id="7df7a-109">プロジェクトにその他のファイルを追加する機能は、いろいろな面で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7df7a-109">There are a number of reasons why it is useful to be able to add miscellaneous files to your project.</span></span> <span data-ttu-id="7df7a-110">たとえば、ソリューションの開発に不可欠ではあっても、必ずしもスクリプトとして認識されているわけではないファイルが存在します。</span><span class="sxs-lookup"><span data-stu-id="7df7a-110">You might have a file that is not necessarily a recognized script but integral to the solution's development.</span></span> <span data-ttu-id="7df7a-111">一般的な例としては、開発に関するメモや指示書、データ ファイル、コードの一部などがあります。</span><span class="sxs-lookup"><span data-stu-id="7df7a-111">Common examples include development notes or instructions, data files, and code clips.</span></span>  
  
 <span data-ttu-id="7df7a-112">その他のファイルを活用すれば、柔軟な対応が可能になります。</span><span class="sxs-lookup"><span data-stu-id="7df7a-112">Miscellaneous files provide flexibility.</span></span> <span data-ttu-id="7df7a-113">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプト プロジェクトに、テーブルやストアド プロシージャをデータベース内に作成するためのスクリプトがいくつかあるとします。</span><span class="sxs-lookup"><span data-stu-id="7df7a-113">For example, suppose you have a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Scripts Project that has several scripts for creation of tables and stored procedures in your database.</span></span> <span data-ttu-id="7df7a-114">また、テーブルのデータ ファイルとして拡張子 .BCP のファイルがいくつかあり、実行用の指示書として README.TXT ファイルがあるとします。</span><span class="sxs-lookup"><span data-stu-id="7df7a-114">You also have several data files for the tables with file extensions .BCP and execution instructions in a README.TXT file.</span></span> <span data-ttu-id="7df7a-115">そのようなデータ ファイルや README ファイルをその他のファイルとしてプロジェクトに追加すれば、プロジェクト システムのソース管理機能や他の機能を活用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7df7a-115">You can attach the data and the README files as miscellaneous files to the project to take advantage of source control and other features of the project system.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="7df7a-116">のメニューやツール バーは、開くファイルの形式に応じて変わるようになっています。</span><span class="sxs-lookup"><span data-stu-id="7df7a-116">menus and toolbars change according to the format of the file you open.</span></span> <span data-ttu-id="7df7a-117">たとえば、テキスト ファイルを開けば、[テキスト エディター] ツール バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7df7a-117">When you open a text file, for example, the Text Editor toolbar appears.</span></span> <span data-ttu-id="7df7a-118">XML スキーマ ファイルを開けば、[XML スキーマ] ツール バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7df7a-118">If you open an XML Schema file, the XML Schema toolbar appears.</span></span> <span data-ttu-id="7df7a-119">XML スキーマを編集しているときに、[テキスト エディター] ツール バーは使用できません。</span><span class="sxs-lookup"><span data-stu-id="7df7a-119">While editing your XML Schema, the Text Editor toolbar is unavailable.</span></span> <span data-ttu-id="7df7a-120">プロジェクト ファイルからその他のファイルに切り替えれば、プロジェクトに関連したコマンドやツール バーがすべてその他のファイルに関連したコマンドやツール バーに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="7df7a-120">When you switch between a project file and a miscellaneous file, all project-related commands and toolbars are replaced by those relevant to the miscellaneous file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7df7a-121">参照</span><span class="sxs-lookup"><span data-stu-id="7df7a-121">See Also</span></span>  
 <span data-ttu-id="7df7a-122">[ソリューションとプロジェクトを管理するファイル](files-that-manage-solutions-and-projects.md) </span><span class="sxs-lookup"><span data-stu-id="7df7a-122">[Files That Manage Solutions and Projects](files-that-manage-solutions-and-projects.md) </span></span>  
 <span data-ttu-id="7df7a-123">[ソリューション &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="7df7a-123">[Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="7df7a-124">プロジェクト (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7df7a-124">Projects &#40;SQL Server Management Studio&#41;</span></span>](projects-sql-server-management-studio.md)  
  
  
