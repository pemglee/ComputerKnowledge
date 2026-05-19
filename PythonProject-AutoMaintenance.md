---
title: Python练习 自动化运维
markmap:
  colorFreezeLevel: 24
---

# Python Linux系统运维

## package: psutil

### 基础

#### CPU

+ Linux command check
  + /proc/cpuinfo
    + [operating]

      ```sh
      ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26]
      └─$ cat /proc/cpuinfo
      processor       : 0
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 0
      cpu cores       : 10
      apicid          : 0
      initial apicid  : 0
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 1
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 0
      cpu cores       : 10
      apicid          : 1
      initial apicid  : 1
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 2
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 1
      cpu cores       : 10
      apicid          : 2
      initial apicid  : 2
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 3
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 1
      cpu cores       : 10
      apicid          : 3
      initial apicid  : 3
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 4
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 2
      cpu cores       : 10
      apicid          : 4
      initial apicid  : 4
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 5
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 2
      cpu cores       : 10
      apicid          : 5
      initial apicid  : 5
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 6
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 3
      cpu cores       : 10
      apicid          : 6
      initial apicid  : 6
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 7
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 3
      cpu cores       : 10
      apicid          : 7
      initial apicid  : 7
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 8
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 4
      cpu cores       : 10
      apicid          : 8
      initial apicid  : 8
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 9
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 4
      cpu cores       : 10
      apicid          : 9
      initial apicid  : 9
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 10
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 5
      cpu cores       : 10
      apicid          : 10
      initial apicid  : 10
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 11
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 5
      cpu cores       : 10
      apicid          : 11
      initial apicid  : 11
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 12
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 6
      cpu cores       : 10
      apicid          : 12
      initial apicid  : 12
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 13
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 6
      cpu cores       : 10
      apicid          : 13
      initial apicid  : 13
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 14
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 7
      cpu cores       : 10
      apicid          : 14
      initial apicid  : 14
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 15
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 7
      cpu cores       : 10
      apicid          : 15
      initial apicid  : 15
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 16
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 8
      cpu cores       : 10
      apicid          : 16
      initial apicid  : 16
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 17
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 8
      cpu cores       : 10
      apicid          : 17
      initial apicid  : 17
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 18
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 9
      cpu cores       : 10
      apicid          : 18
      initial apicid  : 18
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      processor       : 19
      vendor_id       : GenuineIntel
      cpu family      : 6
      model           : 186
      model name      : 13th Gen Intel(R) Core(TM) i9-13900H
      stepping        : 2
      microcode       : 0xffffffff
      cpu MHz         : 2995.213
      cache size      : 24576 KB
      physical id     : 0
      siblings        : 20
      core id         : 9
      cpu cores       : 10
      apicid          : 19
      initial apicid  : 19
      fpu             : yes
      fpu_exception   : yes
      cpuid level     : 28
      wp              : yes
      flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
      vmx flags       : vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
      bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
      bogomips        : 5990.42
      clflush size    : 64
      cache_alignment : 64
      address sizes   : 46 bits physical, 48 bits virtual
      power management:
      
      
      ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26]
      └─$
      ```
  + lscpu
    + [operating]

      ```sh
      ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26]
      └─$ sudo lscpu
      Architecture:             x86_64
        CPU op-mode(s):         32-bit, 64-bit
        Address sizes:          46 bits physical, 48 bits virtual
        Byte Order:             Little Endian
      CPU(s):                   20
        On-line CPU(s) list:    0-19
      Vendor ID:                GenuineIntel
        Model name:             13th Gen Intel(R) Core(TM) i9-13900H
          CPU family:           6
          Model:                186
          Thread(s) per core:   2
          Core(s) per socket:   10
          Socket(s):            1
          Stepping:             2
          BogoMIPS:             5990.42
          Flags:                fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm c
                                onstant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2
                                x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ssbd ibrs ibpb stibp ibrs_enhanc
                                ed tpr_shadow ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsa
                                vec xgetbv1 xsaves avx_vnni vnmi umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capa
                                bilities
      Virtualization features:
        Virtualization:         VT-x
        Hypervisor vendor:      Microsoft
        Virtualization type:    full
      Caches (sum of all):
        L1d:                    480 KiB (10 instances)
        L1i:                    320 KiB (10 instances)
        L2:                     12.5 MiB (10 instances)
        L3:                     24 MiB (1 instance)
      NUMA:
        NUMA node(s):           1
        NUMA node0 CPU(s):      0-19
      Vulnerabilities:
        Gather data sampling:   Not affected
        Itlb multihit:          Not affected
        L1tf:                   Not affected
        Mds:                    Not affected
        Meltdown:               Not affected
        Mmio stale data:        Not affected
        Reg file data sampling: Vulnerable: No microcode
        Retbleed:               Mitigation; Enhanced IBRS
        Spec rstack overflow:   Not affected
        Spec store bypass:      Mitigation; Speculative Store Bypass disabled via prctl
        Spectre v1:             Mitigation; usercopy/swapgs barriers and __user pointer sanitization
        Spectre v2:             Mitigation; Enhanced / Automatic IBRS; IBPB conditional; RSB filling; PBRSB-eIBRS SW sequence; BHI BHI_DIS_S
        Srbds:                  Not affected
        Tsx async abort:        Not affected
      
      ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26]
      └─$
      ```

+ python psutil

  + [code]

    ```python

    ```

