---
layout: menu
title: 资源泄露
permalink: /android/memleak
type: android
---
资源泄露
[拥抱 Android Studio 之五：Gradle 插件开发](http://blog.bugtags.com/2016/03/28/embrace-android-studio-gradle-plugin)

```

		匿名内嵌类{
		}

		反注册函数未按预期被调用

		Native 内存泄漏检测

		https://cloud.tencent.com/developer/article/1362381{

			兜底{

				微信是否在主界面退到后台 且 位于后台的时间超过 30 分钟

				当前时间为凌晨 2～5 点

				不存在前台服务（存在通知栏，音乐播放栏等情况）

				java heap 必须大于当前进程最大可分配的 85% || native 内存大于 800M || vmsize 超过了 4G（微信 32bit）的 85%

				非大量的流量消耗（每分钟不超过 1M） && 进程无大量 CPU 调度情况
			}
		}

		java.lang.OutOfMemoryError: pthread_create (1040KB stack) failed: Out of memory{

			在 linux 中对每个进程可创建的线程数也有一定的限制（/proc/pid/limits）而实际测试中，
			我们也发现不同厂商对这个限制也有所不同，而且当超过系统进程线程数限制时，
			同样会抛出这个类型的 OOM

		}

```
