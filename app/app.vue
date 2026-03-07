<template>
  <UApp>
    <main class="flex flex-col w-full h-screen items-center justify-center">
      <div class="bg-muted/50 border overflow-hidden border-muted flex flex-col rounded-2xl shadow-lg w-lg gap-8">
        <div class="w-full -mb-8">
          <img src="~/assets/images/banner.png" />
        </div>

        <div class="flex flex-col gap-8 p-8">
          <div class="flex flex-col">
            <h1 class="text-2xl text-highlighted font-bold">Kuruwumi Cup 3: OPEN</h1>
            <p class="text-toned">Inscrições abertas!</p>
          </div>
          <div class="grid grid-cols-2 gap-2">
            <InfoCard
              icon="lucide:target"
              icon-class="text-violet-400 bg-violet-400/15"
              title="Rank Range"
              description="#1 - #10.000"
            />
            <InfoCard
              icon="lucide:gamepad-2"
              icon-class="text-pink-400 bg-pink-400/15"
              title="Modo"
              description="osu! Standard"
            />
            <InfoCard
              icon="lucide:trophy"
              icon-class="text-pink-400 bg-pink-400/15"
              title="Formato"
              description="1v1"
            />
            <InfoCard
              icon="lucide:users"
              icon-class="text-violet-400 bg-violet-400/15"
              title="Registrados"
              description="16"
            />
          </div>
          <div class="w-full p-4 border border-muted rounded-lg flex items-start gap-2">
            <span class="text-violet-400 bg-violet-400/15 p-1.5 size-fit rounded-lg flex">
              <UIcon name="lucide:clock-4" size="1.5rem" />
            </span>
            <div class="flex w-full flex-col gap-2">
              <p class="-mt-1.25">
                Registros fecham no dia <span class="font-medium">{{ formattedDate }}</span
                >.
              </p>
              <div class="flex w-full justify-start gap-2">
                <CounterCard :value="timeLeft.days" label="dias" />
                <CounterCard :value="timeLeft.hours" label="horas" />
                <CounterCard :value="timeLeft.minutes" label="minutos" />
                <CounterCard :value="timeLeft.seconds" label="segundos" />
              </div>
            </div>
          </div>
          <div class="w-full flex justify-end">
            <UButton size="lg" label="Login com osu!" icon="simple-icons:osu" class="text-text" />
          </div>
        </div>
      </div>
    </main>
  </UApp>
</template>

<script lang="ts" setup>
useDark();

const targetDate = new Date("2026-04-01T00:00:00"); // Set your target date here following that structure (YYYY-MM-DDTHH:mm:ss)
const formattedDate = useDateFormat(targetDate, "DD/MM/YYYY");
const now = useNow({ interval: 1000 });

const timeLeft = computed(() => {
  const diff = targetDate.getTime() - now.value.getTime();

  if (diff <= 0) {
    return { days: 0, hours: 0, minutes: 0, seconds: 0 };
  }

  const days = Math.floor(diff / (1000 * 60 * 60 * 24));
  const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
  const minutes = Math.floor((diff / (1000 * 60)) % 60);
  const seconds = Math.floor((diff / 1000) % 60);

  return { days, hours, minutes, seconds };
});
</script>
