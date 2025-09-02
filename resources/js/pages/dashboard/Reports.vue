<script setup lang="ts">
import { Head } from '@inertiajs/vue3';
import AppLayout from '@/layouts/AppLayout.vue';
import { type BreadcrumbItem } from '@/types';
import { Separator } from '@/components/ui/separator';
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card';
import { Button } from '@/components/ui/button';

const breadcrumbs: BreadcrumbItem[] = [
  { title: 'Dashboard', href: '/dashboard' },
  { title: 'Reports', href: '/dashboard/reports' },
];

const reports = [
  { title: 'Monthly KPI Summary', period: 'Aug 2025', size: '245 KB' },
  { title: 'User Growth Report', period: 'Q2 2025', size: '310 KB' },
  { title: 'Revenue Breakdown', period: 'YTD', size: '198 KB' },
];
</script>

<template>
  <AppLayout :breadcrumbs="breadcrumbs">
    <Head title="Dashboard – Reports" />

    <div class="block sm:flex items-center justify-between px-6 mt-4">
      <div class="flex space-x-1">
        <Button as-child size="sm" variant="ghost"><a href="/dashboard">Overview</a></Button>
        <Button as-child size="sm" variant="ghost"><a href="/dashboard/analytics">Analytics</a></Button>
        <Button as-child size="sm" variant="default"><a href="/dashboard/reports">Reports</a></Button>
      </div>
      <Button variant="default" size="sm">New Report</Button>
    </div>

    <Separator class="my-4" />

    <div class="px-6 pb-6 space-y-6">
      <Card>
        <CardHeader>
          <CardTitle>Saved Reports</CardTitle>
          <CardDescription>Download and manage your reports</CardDescription>
        </CardHeader>
        <CardContent>
          <div class="divide-y">
            <div v-for="r in reports" :key="r.title" class="flex items-center justify-between py-3">
              <div>
                <p class="font-medium">{{ r.title }}</p>
                <p class="text-xs text-muted-foreground">{{ r.period }} • {{ r.size }}</p>
              </div>
              <div class="space-x-2">
                <Button variant="outline" size="sm">Preview</Button>
                <Button variant="default" size="sm">Download</Button>
              </div>
            </div>
          </div>
        </CardContent>
      </Card>
    </div>
  </AppLayout>
</template>

