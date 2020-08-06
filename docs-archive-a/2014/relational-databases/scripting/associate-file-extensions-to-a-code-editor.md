---
title: ファイル拡張子をコード エディターに関連付ける方法
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- file extensions [SQL Server]
- associating file extensions [SQL Server]
- Query Editor [SQL Server Management Studio], associating file extensions
ms.assetid: 193630f4-93de-4950-8f36-68702531f925
author: rothja
ms.author: jroth
ms.openlocfilehash: 0e8cfbc89892a99971e985ffd3ff10b99f89fe53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634922"
---
# <a name="associate-file-extensions-to-a-code-editor"></a><span data-ttu-id="cb45c-102">ファイル拡張子をコード エディターに関連付ける方法</span><span class="sxs-lookup"><span data-stu-id="cb45c-102">Associate File Extensions to a Code Editor</span></span>
  <span data-ttu-id="cb45c-103">ファイル拡張子を特定のコード エディターに関連付けると、Windows エクスプローラーでファイルをダブルクリックしたときに、対応する [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] コード エディターでそのファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="cb45c-103">Associating file extensions to a specific code editor allows you to open a file with the appropriate [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] code editor when you double-click a file in Windows Explorer.</span></span> <span data-ttu-id="cb45c-104">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でよく使用される .sql や .mdx などの拡張子は、インストール時に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="cb45c-104">The extensions commonly used by [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], such as .sql and .mdx, are associated during installation.</span></span> <span data-ttu-id="cb45c-105">また、新しいファイル拡張子は、ファイル システム内で [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] に関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb45c-105">New file extensions must also be associated to [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] in the file system.</span></span> <span data-ttu-id="cb45c-106">この機能を使用して、他のエディターで作成されたファイルを開くことができます。また、.bak という名前に変更された .sql ファイルのバックアップなど、名前が変更されたファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="cb45c-106">You can use this feature to open files created with other editors, or to open files you have renamed, such as backups of .sql files that were renamed .bak.</span></span>  
  
 <span data-ttu-id="cb45c-107">この操作には 2 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="cb45c-107">There are two steps in the process.</span></span> <span data-ttu-id="cb45c-108">まず拡張子を [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]に関連付け、次に特定のコード エディターに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="cb45c-108">First associate the extension with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then associate the extension with a specific code editor.</span></span>  
  
### <a name="to-associate-a-new-file-extension-with-sql-server-management-studio"></a><span data-ttu-id="cb45c-109">新しいファイル拡張子を SQL Server Management Studio に関連付けるには</span><span class="sxs-lookup"><span data-stu-id="cb45c-109">To associate a new file extension with SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="cb45c-110">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[アクセサリ]** の順にポイントして、 **[エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb45c-110">On the **Start** menu, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
2.  <span data-ttu-id="cb45c-111">Windows エクスプローラーで、 **[ツール]** メニューの **[フォルダー オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb45c-111">In Windows Explorer, on the **Tools** menu, click **Folder Options**.</span></span>  
  
3.  <span data-ttu-id="cb45c-112">**[フォルダー オプション]** ダイアログ ボックスで、 **[ファイルの種類]** タブの **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb45c-112">In the **Folder Options** dialog box, on the **File Types** tab, click **New**.</span></span>  
  
4.  <span data-ttu-id="cb45c-113">**[新しい拡張子の作成]** ダイアログ ボックスで、関連付ける新しいファイル拡張子を **[ファイルの拡張子]** ボックスに入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb45c-113">In the **Create New Extension** dialog box, in the **File Extension** box, type the new file extension that you want to associate, and then click **OK**.</span></span> <span data-ttu-id="cb45c-114">拡張子の先頭にピリオドを付けないでください。</span><span class="sxs-lookup"><span data-stu-id="cb45c-114">Do not start the extension with a period.</span></span>  
  
5.  <span data-ttu-id="cb45c-115">**[登録されているファイルの種類]** ボックスで、新しい拡張子をクリックし、 **[変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb45c-115">In the **Registered file** types box, click on your new extension, and then click **Change**.</span></span>  
  
6.  <span data-ttu-id="cb45c-116">**[ファイルを開くプログラムの選択]** ダイアログ ボックスで **[SSMS - SQL Server Management Studio]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb45c-116">In the **Open With** dialog box, click **SSMS - SQL Server Management Studio**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="cb45c-117">**[閉じる]** をクリックして **[フォルダー オプション]** ダイアログ ボックスを閉じ、Windows エクスプローラーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="cb45c-117">Click **Close** to close the **Folder Options** dialog box, and then close Windows Explorer.</span></span>  
  
### <a name="to-associate-a-new-file-extension-with-a-code-editor-in-sql-server-management-studio"></a><span data-ttu-id="cb45c-118">新しいファイル拡張子を SQL Server Management Studio のコード エディターに関連付けるには</span><span class="sxs-lookup"><span data-stu-id="cb45c-118">To associate a new file extension with a code editor in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="cb45c-119">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb45c-119">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], from the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="cb45c-120">**[オプション]** ダイアログ ボックスで、 **[テキスト エディター]** 、 **[ファイル拡張子]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb45c-120">In the **Options** dialog box, click **Text Editor**, and then click **File Extension**.</span></span>  
  
3.  <span data-ttu-id="cb45c-121">**[拡張子]** ボックスに新しいファイル拡張子を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb45c-121">In the **Extension** box, type your new file extension.</span></span>  
  
4.  <span data-ttu-id="cb45c-122">**[エディター]** ボックスで、この種類のファイルを開くときに使用するコード エディターをクリックし、 **[追加]** 、 **[OK]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb45c-122">In the **Editor** box, click the code editor that you wish to use to open this file type, click **Add**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb45c-123">参照</span><span class="sxs-lookup"><span data-stu-id="cb45c-123">See Also</span></span>  
 [<span data-ttu-id="cb45c-124">Ssms ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="cb45c-124">Ssms Utility</span></span>](../../ssms/ssms-utility.md)  
  
  
