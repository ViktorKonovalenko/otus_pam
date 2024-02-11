1) Запретить всем пользователям, кроме группы admin, логин в выходные (суббота и воскресенье), без учета праздников<br
<h2>Решение:<h2><br>
Запускаем vagrant в котором настроен ansible playbook, для создания пользователя, создания группы, добавления в эту группу пользователей, создания скрипта для доступа по выходным и редактирования pam.d
<pre>vagrant up</pre>
Проверяем доступ пользователей по ssh(дз выполняется в выходной день)
<pre>
viktor@viktor-VirtualBox:~/otus_pam$ date
Вс 11 фев 2024 17:20:25 +07
</pre>
Пользователь otusadm
<pre>
viktor@viktor-VirtualBox:~/otus_pam$ ssh otusadm@192.168.57.10
otusadm@192.168.57.10's password:
Last login: Sun Feb 11 08:55:22 2024 from 192.168.57.1
[otusadm@pam ~]$
</pre>
Пользователь otus
<pre>
viktor@viktor-VirtualBox:~/otus_pam$ ssh otus@192.168.57.10
otus@192.168.57.10's password:
Permission denied, please try again.
otus@192.168.57.10's password:
Permission denied, please try again.
otus@192.168.57.10's password:
otus@192.168.57.10: Permission denied (publickey,gssapi-keyex,gssapi-with-mic,password).
viktor@viktor-VirtualBox:~/otus_pam$
</pre>
Пользователь otusadm получает доступ т.к он входит в группу admin, а пользователь otus не получает т.к. не входит в группу. 


