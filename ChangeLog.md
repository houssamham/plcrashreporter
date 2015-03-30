### 1.1-RC2 (12/11/2012) ###

Bug fixes:

  * The output of the PLCrashReportTextFormatter was modified for compatibility with Xcode 4.5.2 symbolication.
  * ARMv7 text rendering fix: ARMv7 binaries were incorrectly reported as "unknown" when reports were rendered with the PLCrashReportTextFormatter.

### 1.1-RC1 (11/28/2012) ###

  * Adds [-[PLCrashReporter generateLiveReport](http://plcrashreporter.googlecode.com/svn/tags/plcrashreporter-1.1-rc1/Documentation/API/interface_p_l_crash_reporter.html#a218c870c9be7d6a02ac58734b27cabfd)], to allow generating a report on-demand. The current thread's state is captured by an assembly trampoline, and then written to the generated report.
  * [Additional machine data](http://plcrashreporter.googlecode.com/svn/tags/plcrashreporter-1.1-rc1/Documentation/API/interface_p_l_crash_report_machine_info.html) is now available from a PLCrashReport, including the number available processors, and specific CPU type/subtype data.
  * Adds ARMv7s support.
  * ARMv6 binaries are no longer provided, as Apple is no longer providing an armv6 compiler. ARMv6 remains supported by the crash reporter, and users may build their own ARMv6 binaries.

### 1.2 (TBD) ###

  * Client-side symbolication using both non-stripped symbols and available runtime metadata.
  * Initial support for out-of-process execution on systems where fork() is permitted (Mac OS X)
  * DWARF-based stack walking (required for x86-64)