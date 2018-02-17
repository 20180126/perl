## Docucument

***

- 変数

```pl

# 配列変数
@array = ('hoge','foo','bar');

# @以外の変数にはmyで変数宣言しなければならない

# スカラー変数,ダイアモンド演算子
my $line = <FILE>

# 分割代入
my ($sec, $min, $hour, $mday, $mon, $year) = localtime;

# 文字連結
my $optionStr = $year."/".$mon."/".$mday." ".$hour.":".$min.":".$sec;

# 数値計算
$year += 1900;
$mon++;

```

- 正規表現

```pl

# 一致を指定
my $obj =~ /[a-zA-Z1-9!~^]/;

# 不一致を指定
my $obj !~ /[a-zA-Z1-0!~^]/;

```

- エンコード

```pl

# ファイルの読み込み

use open ":utf8";
use open IO => qw/:encoding(UTF-8)/;
binmode STDOUT, ':encoding(UTF-8)';

# HTML出力

print qq(Content-type: text/html\n\n);
print <<END;
    <html lang="ja">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Document</title>
        <link rel="stylesheet" href="./style.css">
    </head>
END

# 文字列出力

my $cgi = new CGI;
$cgi->charset('utf-8');
$cgi->escapeHTML($foo);

# PerlはデフォルトではSJISのため読み込み、書き込みの際にエスケープを行わなければならない

```

- モジュール

```pl

use strict;
use warnings;
use utf8;
use CGI;

# DB

use DBI;

my $DB_NAME = "";
my $DB_USER = "";
my $DB_PASS = "";

my $dbh = DBI->connect("dbi:Pg:dbname=$DB_NAME;", $DB_USER, $DB_PASS)
          or die "$!\n Error: failed to connect to DB.\n";
my $sth = $dbh->prepare("SELECT * FROM pg_authid");
$sth->execute();

```