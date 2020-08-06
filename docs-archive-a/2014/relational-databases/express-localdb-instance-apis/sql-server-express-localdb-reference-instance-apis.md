---
title: SQL Server Express LocalDB インスタンスの API リファレンス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: faec46da-0536-4de3-96f3-83e607c8a8b6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5934bc5159998db22d7c560b31457524773e74eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711930"
---
# <a name="sql-server-express-localdb-instance-api-reference"></a><span data-ttu-id="39d6b-102">SQL Server Express LocalDB のインスタンス API リファレンス</span><span class="sxs-lookup"><span data-stu-id="39d6b-102">SQL Server Express LocalDB Instance API Reference</span></span>
  <span data-ttu-id="39d6b-103">従来のサービスベースの SQL Server 環境で、単一のコンピューターにインストールされた個々の SQL Server インスタンスは、物理的に独立しています。つまり、各インスタンスは独立したバイナリ セットを持っており、独立したサービス プロセスの下で実行されます。インストールと削除も個別に行われる必要があります。</span><span class="sxs-lookup"><span data-stu-id="39d6b-103">In the traditional, service-based SQL Server world, individual SQL Server instances installed on a single computer are physically separated; that is, each instance must be installed and removed separately, has a separate set of binaries, and runs under a separate service process.</span></span> <span data-ttu-id="39d6b-104">ユーザーが接続する先の SQL Server インスタンスは、SQL Server インスタンス名を使用して指定されます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-104">The SQL Server instance name is used to specify which SQL Server instance the user wants to connect to.</span></span>  
  
 <span data-ttu-id="39d6b-105">SQL Server Express LocalDB インスタンス API は、簡略化された "軽量な" インスタンスモデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-105">The SQL Server Express LocalDB instance API uses a simplified, "light" instance model.</span></span> <span data-ttu-id="39d6b-106">個々の LocalDB インスタンスは、ディスク上とレジストリ内で独立していますが、同じ 1 組の共有 LocalDB バイナリを使用します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-106">Although individual LocalDB instances are separated on the disk and in the registry, they use the same set of shared LocalDB binaries.</span></span> <span data-ttu-id="39d6b-107">また、LocalDB ではサービスが使用されません。LocalDB インスタンスは、LocalDB インスタンス API 呼び出しを介して要求時に起動されます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-107">Moreover, LocalDB does not use services; LocalDB instances are launched on demand through LocalDB instance API calls.</span></span> <span data-ttu-id="39d6b-108">LocalDB では、ユーザーが使用する LocalDB インスタンスを指定するために、インスタンス名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-108">In LocalDB, the instance name is used to specify which of the LocalDB instances the user wants to work with.</span></span>  
  
 <span data-ttu-id="39d6b-109">LocalDB インスタンスは、常に1人のユーザーによって所有され、インスタンス共有が有効になっている場合を除き、このユーザーのコンテキストからのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-109">A LocalDB instance is always owned by a single user and is visible and accessible only from this user's context, unless instance sharing is enabled.</span></span>  
  
 <span data-ttu-id="39d6b-110">厳密には、LocalDB インスタンスは従来の SQL Server インスタンスとは異なりますが、意図されている用途はほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="39d6b-110">Although technically LocalDB instances are not the same as traditional SQL Server instances, their intended use is similar.</span></span> <span data-ttu-id="39d6b-111">これらは*インスタンス*と呼ばれ、この類似性を強調し、SQL Server ユーザーにとって直観的にするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-111">They are called *instances* to emphasize this similarity and to make them more intuitive to SQL Server users.</span></span>  
  
 <span data-ttu-id="39d6b-112">LocalDB では、自動インスタンス (AI) と名前付きインスタンス (NI) という 2 種類のインスタンスがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="39d6b-112">LocalDB supports two kinds of instances: automatic instances (AI) and named instances (NI).</span></span> <span data-ttu-id="39d6b-113">LocalDB インスタンスの識別子は、インスタンス名です。</span><span class="sxs-lookup"><span data-stu-id="39d6b-113">The identifier for a LocalDB instance is the instance name.</span></span>  
  
## <a name="automatic-localdb-instances"></a><span data-ttu-id="39d6b-114">自動 LocalDB インスタンス</span><span class="sxs-lookup"><span data-stu-id="39d6b-114">Automatic LocalDB Instances</span></span>  
 <span data-ttu-id="39d6b-115">自動 LocalDB インスタンスは "パブリック" です。ユーザーに対して自動的に作成および管理され、任意のアプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-115">Automatic LocalDB instances are "public"; they are created and managed automatically for the user and can be used by any application.</span></span> <span data-ttu-id="39d6b-116">ユーザーのコンピューターにインストールされている LocalDB のバージョンごとに、1つの自動 LocalDB インスタンスが存在します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-116">One automatic LocalDB instance exists for every version of LocalDB that is installed on the user's computer.</span></span>  
  
 <span data-ttu-id="39d6b-117">自動 LocalDB インスタンスを使用すると、シームレスなインスタンス管理を実行できます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-117">Automatic LocalDB instances provide seamless instance management.</span></span> <span data-ttu-id="39d6b-118">ユーザーがインスタンスを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="39d6b-118">The user does not need to create the instance.</span></span> <span data-ttu-id="39d6b-119">これにより、ユーザーはアプリケーションのインストールや、複数の異なるコンピューターへの移行を容易に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-119">This enables users to easily install applications and to migrate to different computers.</span></span> <span data-ttu-id="39d6b-120">ターゲット コンピューターに指定バージョンの LocalDB がインストールされている場合、そのコンピューターでは、同じバージョンの自動 LocalDB インスタンスも使用できます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-120">If the target computer has the specified version of LocalDB installed, the automatic LocalDB instance for that version is also available on that computer.</span></span>  
  
### <a name="automatic-instance-management"></a><span data-ttu-id="39d6b-121">自動インスタンス管理</span><span class="sxs-lookup"><span data-stu-id="39d6b-121">Automatic Instance Management</span></span>  
 <span data-ttu-id="39d6b-122">ユーザーは、自動 LocalDB インスタンスを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="39d6b-122">A user does not need to create an automatic LocalDB instance.</span></span> <span data-ttu-id="39d6b-123">指定されたバージョンの LocalDB がユーザーのコンピューターで使用可能な場合は、インスタンスの初回使用時にインスタンスが遅延作成されます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-123">The instance is lazily created the first time the instance is used, provided that the specified version of LocalDB is available on the user's computer.</span></span> <span data-ttu-id="39d6b-124">ユーザーの視点から見ると、LocalDB バイナリが存在する場合、自動インスタンスは常に存在します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-124">From the user's point of view, the automatic instance is always present if the LocalDB binaries are present.</span></span>  
  
 <span data-ttu-id="39d6b-125">自動インスタンスには、削除、共有、共有解除など、その他のインスタンス管理操作も使用できます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-125">Other instance management operations, such as Delete, Share, and Unshare, also work for automatic instances.</span></span> <span data-ttu-id="39d6b-126">特に、自動インスタンスを削除すると、そのインスタンスが効果的にリセットされ、次回の起動操作時に再作成されます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-126">In particular, deleting an automatic instance effectively resets the instance, which will be re-created on the next Start operation.</span></span> <span data-ttu-id="39d6b-127">システム データベースが破損した場合は、自動インスタンスの削除が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="39d6b-127">Deleting an automatic instance may be required if the system databases become corrupted.</span></span>  
  
### <a name="automatic-instance-naming-rules"></a><span data-ttu-id="39d6b-128">自動インスタンスの名前付け規則</span><span class="sxs-lookup"><span data-stu-id="39d6b-128">Automatic Instance Naming Rules</span></span>  
 <span data-ttu-id="39d6b-129">自動 LocalDB インスタンスのインスタンス名には特殊なパターンがあり、これは予約済み名前空間に属します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-129">Automatic LocalDB instances have a special pattern for the instance name that belongs to a reserved namespace.</span></span> <span data-ttu-id="39d6b-130">このようなパターンが必要になるのは、名前付き LocalDB インスタンスと名前が競合するのを防ぐためです。</span><span class="sxs-lookup"><span data-stu-id="39d6b-130">This is necessary to prevent name conflicts with named LocalDB instances.</span></span>  
  
 <span data-ttu-id="39d6b-131">自動インスタンス名は、LocalDB のベースラインリリースバージョン番号で、前に1つの "v" 文字が付いています。</span><span class="sxs-lookup"><span data-stu-id="39d6b-131">The automatic instance name is the LocalDB baseline release version number preceded by a single "v" character.</span></span> <span data-ttu-id="39d6b-132">これは "v" のように、2つの数値の間にピリオドを加えたものです。たとえば、「v 11.0」や「-12.00」のようにします。</span><span class="sxs-lookup"><span data-stu-id="39d6b-132">This looks like "v" plus two numbers with a period between them; for example, v11.0 or V12.00.</span></span>  
  
 <span data-ttu-id="39d6b-133">無効な自動インスタンス名の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-133">Examples of illegal automatic instance names are:</span></span>  
  
-   <span data-ttu-id="39d6b-134">11.0 (先頭に "v" 文字がありません)</span><span class="sxs-lookup"><span data-stu-id="39d6b-134">11.0 (missing the "v" character at the beginning)</span></span>  
  
-   <span data-ttu-id="39d6b-135">v11 (ピリオドと 2 番目のバージョン番号がありません)</span><span class="sxs-lookup"><span data-stu-id="39d6b-135">v11 (missing a period and the second number of the version)</span></span>  
  
-   <span data-ttu-id="39d6b-136">v11.</span><span class="sxs-lookup"><span data-stu-id="39d6b-136">v11.</span></span> <span data-ttu-id="39d6b-137">(2 番目のバージョン番号がありません)</span><span class="sxs-lookup"><span data-stu-id="39d6b-137">(missing the second number of the version)</span></span>  
  
-   <span data-ttu-id="39d6b-138">v11.0.1.2 (バージョン番号の数が 2 つを超えています)</span><span class="sxs-lookup"><span data-stu-id="39d6b-138">v11.0.1.2 (version number has more than two parts)</span></span>  
  
## <a name="named-localdb-instances"></a><span data-ttu-id="39d6b-139">名前付き LocalDB インスタンス</span><span class="sxs-lookup"><span data-stu-id="39d6b-139">Named LocalDB Instances</span></span>  
 <span data-ttu-id="39d6b-140">名前付き LocalDB インスタンスは "プライベート" です。インスタンスは、インスタンスの作成と管理を担当する1つのアプリケーションによって所有されます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-140">Named LocalDB instances are "private"; an instance is owned by a single application that is responsible for creating and managing the instance.</span></span> <span data-ttu-id="39d6b-141">名前付き LocalDB インスタンスを使用すると、そのインスタンスを分離することで、パフォーマンスの向上を図ることができます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-141">Named LocalDB instances provide isolation and improve performance.</span></span>  
  
### <a name="named-instance-creation"></a><span data-ttu-id="39d6b-142">名前付きインスタンスの作成</span><span class="sxs-lookup"><span data-stu-id="39d6b-142">Named Instance Creation</span></span>  
 <span data-ttu-id="39d6b-143">名前付きインスタンスは、ユーザーが LocalDB 管理 API を通じて明示的に作成するか、マネージド アプリケーションの app.config ファイルを通じて暗黙的に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39d6b-143">The user must create named instances explicitly through the LocalDB management API, or implicitly through the app.config file for a managed application.</span></span> <span data-ttu-id="39d6b-144">この API は、マネージド アプリケーションでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-144">A managed application may also use the API.</span></span>  
  
 <span data-ttu-id="39d6b-145">各名前付きインスタンスには、特定の LocalDB バージョンが関連付けらています。つまり、各名前付きインスタンスは、LocalDB バイナリの特定のセットを指しています。</span><span class="sxs-lookup"><span data-stu-id="39d6b-145">Each named instance has an associated LocalDB version; that is, it points to a specified set of LocalDB binaries.</span></span> <span data-ttu-id="39d6b-146">名前付きインスタンスのバージョンは、インスタンス作成時に設定されます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-146">The version for the named instance is set during the instance creation process.</span></span>  
  
### <a name="named-instance-naming-rules"></a><span data-ttu-id="39d6b-147">名前付きインスタンスの名前付け規則</span><span class="sxs-lookup"><span data-stu-id="39d6b-147">Named Instance Naming Rules</span></span>  
 <span data-ttu-id="39d6b-148">LocalDB インスタンス名の最大文字数は 128 文字です (これは `sysname` データ型による制約です)。</span><span class="sxs-lookup"><span data-stu-id="39d6b-148">A LocalDB instance name can have up to a total of 128 characters (the limit is imposed by the `sysname` data type).</span></span> <span data-ttu-id="39d6b-149">これは、従来の SQL Server インスタンス名と比較すると、大きく異なります。従来は、16 の ASCII 文字で構成される NetBIOS 名に制限されていました。</span><span class="sxs-lookup"><span data-stu-id="39d6b-149">This is a significant difference compared to traditional SQL Server instance names, which are limited to NetBIOS names of 16 ASCII characters.</span></span> <span data-ttu-id="39d6b-150">この違いの理由は、LocalDB ではデータベースがファイルとして扱われるため、ファイルベースのセマンティクスを意味するので、ユーザーはより自由にインスタンス名を選択できます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-150">The reason for this difference is that LocalDB treats databases as files, and therefore implies file-based semantics, so it's intuitive for users to have more freedom in choosing instance names.</span></span>  
  
 <span data-ttu-id="39d6b-151">LocalDB のインスタンス名には、ファイル名コンポーネント内で有効な任意の Unicode 文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-151">A LocalDB instance name can contain any Unicode characters that are legal within the filename component.</span></span> <span data-ttu-id="39d6b-152">ファイル名コンポーネント内の無効な文字には、通常、ASCII/Unicode 文字 1 ~ 31 の文字、引用符 (")、小なり ( \<), greater than (> )、パイプ (|)、バックスペース (\b)、タブ (\t)、コロン (:)、アスタリスク (\*)、疑問符 (?)、円記号 ( \\ )、およびスラッシュ (/) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-152">Illegal characters in a filename component generally include the following characters: ASCII/Unicode characters 1 through 31, as well as quote ("), less than (\<), greater than (>), pipe (|), backspace (\b), tab (\t), colon (:), asterisk (\*), question mark (?), backslash (\\), and forward slash (/).</span></span> <span data-ttu-id="39d6b-153">null 文字 (\0) は、文字列の終端として許可されています。最初に検出された null 文字以降は、すべての文字が無視されます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-153">Note that the null character (\0) is allowed because it is used for string termination; everything after the first null character will be ignored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39d6b-154">無効な文字はオペレーティング システムによって異なり、今後のリリースで変わることもあります。</span><span class="sxs-lookup"><span data-stu-id="39d6b-154">The list of illegal characters may depend on the operating system and may change in future releases.</span></span>  
  
 <span data-ttu-id="39d6b-155">インスタンス名の先頭と末尾の空白は無視され、トリミングされます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-155">Leading and trailing white spaces in instance names are ignored and will be trimmed.</span></span>  
  
 <span data-ttu-id="39d6b-156">名前の競合を回避するには、「自動インスタンスの名前付け規則」で既に説明したように、名前付き LocalDB インスタンスには自動インスタンスの名前付けパターンに従った名前を付けることはできません。</span><span class="sxs-lookup"><span data-stu-id="39d6b-156">To avoid naming conflicts, named LocalDB instances cannot have a name that follows the naming pattern for automatic instances, as described earlier in "Automatic Instance Naming Rules."</span></span> <span data-ttu-id="39d6b-157">自動インスタンスの名前付けパターンに従った名前の名前付きインスタンスを作成しようとすると、既定のインスタンスが実質的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="39d6b-157">An attempt to create a named instance with a name that follows the automatic instance naming pattern effectively creates a default instance.</span></span>  
  
## <a name="sql-server-express-localdb-reference-topics"></a><span data-ttu-id="39d6b-158">SQL Server Express LocalDB リファレンス トピック</span><span class="sxs-lookup"><span data-stu-id="39d6b-158">SQL Server Express LocalDB Reference Topics</span></span>  
 [<span data-ttu-id="39d6b-159">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="39d6b-159">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
 <span data-ttu-id="39d6b-160">LocalDB インスタンス API を見つけるためのヘッダー ファイル情報とレジストリ キーを提供します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-160">Provides header file information and registry keys for finding the LocalDB instance API.</span></span>  
  
 [<span data-ttu-id="39d6b-161">コマンドライン管理ツール:SqlLocalDB.exe</span><span class="sxs-lookup"><span data-stu-id="39d6b-161">Command-Line Management Tool: SqlLocalDB.exe</span></span>](command-line-management-tool-sqllocaldb-exe.md)  
 <span data-ttu-id="39d6b-162">コマンド ラインから LocalDB インスタンスを管理するツールである SqlLocalDB.exe について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-162">Describes SqlLocalDB.exe, a tool for managing LocalDB instances from the command line.</span></span>  
  
 [<span data-ttu-id="39d6b-163">LocalDBCreateInstance 関数</span><span class="sxs-lookup"><span data-stu-id="39d6b-163">LocalDBCreateInstance Function</span></span>](localdbcreateinstance-function.md)  
 <span data-ttu-id="39d6b-164">LocalDB インスタンスを新規作成するための関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-164">Describes the function to create a new LocalDB instance.</span></span>  
  
 [<span data-ttu-id="39d6b-165">LocalDBDeleteInstance 関数</span><span class="sxs-lookup"><span data-stu-id="39d6b-165">LocalDBDeleteInstance Function</span></span>](localdbdeleteinstance-function.md)  
 <span data-ttu-id="39d6b-166">LocalDB インスタンスを削除する関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-166">Describes the function to remove a LocalDB instance.</span></span>  
  
 [<span data-ttu-id="39d6b-167">LocalDBFormatMessage 関数</span><span class="sxs-lookup"><span data-stu-id="39d6b-167">LocalDBFormatMessage Function</span></span>](localdbformatmessage-function.md)  
 <span data-ttu-id="39d6b-168">LocalDB エラーのローカライズされた説明を返す関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-168">Describes the function to return the localized description for a LocalDB error.</span></span>  
  
 [<span data-ttu-id="39d6b-169">LocalDBGetInstanceInfo 関数</span><span class="sxs-lookup"><span data-stu-id="39d6b-169">LocalDBGetInstanceInfo Function</span></span>](localdbgetinstanceinfo-function.md)  
 <span data-ttu-id="39d6b-170">LocalDB インスタンスの情報 (バージョン情報、存在するかどうか、実行中かどうかなど) を取得する関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-170">Describes the function to get information for a LocalDB instance, such as whether it exists, version information, whether it is running, and so on.</span></span>  
  
 [<span data-ttu-id="39d6b-171">LocalDBGetInstances 関数</span><span class="sxs-lookup"><span data-stu-id="39d6b-171">LocalDBGetInstances Function</span></span>](localdbgetinstances-function.md)  
 <span data-ttu-id="39d6b-172">指定されたバージョンの LocalDB インスタンスをすべて返す関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-172">Describes the function to return all the LocalDB instances with a specified version.</span></span>  
  
 [<span data-ttu-id="39d6b-173">LocalDBGetVersionInfo 関数</span><span class="sxs-lookup"><span data-stu-id="39d6b-173">LocalDBGetVersionInfo Function</span></span>](localdbgetversioninfo-function.md)  
 <span data-ttu-id="39d6b-174">指定された LocalDB バージョンの情報を返す関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-174">Describes the function to return information for a specified LocalDB version.</span></span>  
  
 [<span data-ttu-id="39d6b-175">LocalDBGetVersions 関数</span><span class="sxs-lookup"><span data-stu-id="39d6b-175">LocalDBGetVersions Function</span></span>](localdbgetversions-function.md)  
 <span data-ttu-id="39d6b-176">コンピューターにインストールされているすべての LocalDB バージョンを返す関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-176">Describes the function to return all LocalDB versions available on a computer.</span></span>  
  
 [<span data-ttu-id="39d6b-177">LocalDBShareInstance 関数</span><span class="sxs-lookup"><span data-stu-id="39d6b-177">LocalDBShareInstance Function</span></span>](localdbshareinstance-function.md)  
 <span data-ttu-id="39d6b-178">指定された LocalDB インスタンスを共有するための関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-178">Describes the function to share a specified LocalDB instance.</span></span>  
  
 [<span data-ttu-id="39d6b-179">LocalDBStartInstance 関数</span><span class="sxs-lookup"><span data-stu-id="39d6b-179">LocalDBStartInstance Function</span></span>](localdbstartinstance-function.md)  
 <span data-ttu-id="39d6b-180">指定された LocalDB インスタンスを起動する関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-180">Describes the function to start a specified LocalDB instance.</span></span>  
  
 [<span data-ttu-id="39d6b-181">LocalDBStartTracing 関数</span><span class="sxs-lookup"><span data-stu-id="39d6b-181">LocalDBStartTracing Function</span></span>](localdbstarttracing-function.md)  
 <span data-ttu-id="39d6b-182">ユーザーの API トレースを有効にする関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-182">Describes the function to enable API tracing for a user.</span></span>  
  
 [<span data-ttu-id="39d6b-183">LocalDBStopInstance 関数</span><span class="sxs-lookup"><span data-stu-id="39d6b-183">LocalDBStopInstance Function</span></span>](localdbstopinstance-function.md)  
 <span data-ttu-id="39d6b-184">指定された LocalDB インスタンスの実行を停止する関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-184">Describes the function to stop a specified LocalDB instance from running.</span></span>  
  
 [<span data-ttu-id="39d6b-185">LocalDBStopTracing 関数</span><span class="sxs-lookup"><span data-stu-id="39d6b-185">LocalDBStopTracing Function</span></span>](localdbstoptracing-function.md)  
 <span data-ttu-id="39d6b-186">ユーザーの API トレースを無効にする関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-186">Describes the function to disable API tracing for a user.</span></span>  
  
 [<span data-ttu-id="39d6b-187">LocalDBUnshareInstance 関数</span><span class="sxs-lookup"><span data-stu-id="39d6b-187">LocalDBUnshareInstance Function</span></span>](localdbunshareinstance-function.md)  
 <span data-ttu-id="39d6b-188">指定された LocalDB インスタンスの共有を停止する関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d6b-188">Describes the function to stop sharing a specified LocalDB instance.</span></span>  
  
  
