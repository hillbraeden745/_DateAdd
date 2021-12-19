# _DateAdd
nclude &lt;Date.au3> #include &lt;MsgBoxConstants.au3> #AutoIt3Wrapper_AU3Check_Parameters=-w 3 -w 4 -w 5 -w 6 -d ; CarlD rev. 2021-09-25  Global $sDate1 = "2199/12/31 23:59:59"; later date Global $sDate2 = "1900/01/01 00:00:01"; earlier date (default = now)  MsgBox( $MB_SYSTEMMODAL, @ScriptName, "Difference is:" &amp; @LF &amp; _DateDiffWords($sDate1) ); $sDate2  Func _DateDiffWords($date1, $date2 = @YEAR &amp; "/" &amp; @MON &amp; "/" &amp; @MDAY &amp; " " &amp; @HOUR &amp; ":" &amp; @MIN &amp; ":" &amp; @SEC) ; Reports difference between two dates in words ; #include &lt;Date.au3> ; $date1 = YYYY/MM/DD[ hh:mm[:ss]]     Local $sDiffOut = ""     Local $sYear = "year", $sMon = "month", $sWeek = "week", $sDay = "day"     Local $sHour = "hour", $sMin = "minute", $sSec = "second"     Local $sAnd = "and"     Local $Y, $M, $W, $D, $H, $N, $S; _DateDiff types     $Y = _DateDiff("Y", $date2, $date1)     If $Y Then         $sDiffOut = $Y &amp; " " &amp; _OneMany($sYear, $Y)         $date1 = _DateAdd("Y", -1 * $Y, $date1)     EndIf     $M = _DateDiff("M", $date2, $date1)     If $M Then         If $sDiffOut Then $sDiffOut &amp;= ", "         $sDiffOut &amp;= $M &amp; " " &amp; _OneMany($sMon, $M)         $date1 = _DateAdd("M", -1 * $M, $date1)     EndIf     $W = _DateDiff("W", $date2, $date1)     If $W Then         If $sDiffOut Then $sDiffOut &amp;= ", "         $sDiffOut &amp;= $W &amp; " " &amp; _OneMany($sWeek, $W)         $date1 = _DateAdd("W", -1 * $W, $date1)     EndIf     $D = _DateDiff("D", $date2, $date1)
