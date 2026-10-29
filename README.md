# Cachapas Maracay — Pedidos online con Webpay y KDS

🔗 **En producción:** https://cachapasmaracay.cl

Sistema de pedidos online para un restaurante venezolano con 3 sedes en Chile (Santiago Centro, Providencia y Viña del Mar). Procesa **pagos reales** todos los días.

> El código fuente es privado porque pertenece al cliente. Este repositorio documenta el proyecto.

## Funcionalidades
- **Pedidos y pago:** el cliente elige sede, arma su carrito y paga con **Webpay Plus** (retiro, mesa o delivery).
- **KDS (Kitchen Display System):** cada sede ve sus pedidos pagados en tiempo real (pendiente → en cocina → listo → entregado). Funciona como PWA con notificaciones push.
- **Panel admin:** ventas del día de las 3 sedes y auditoría de pedidos.
- **Delivery:** cobro por km de ruta o por zona según la sede, con mapa interactivo.
- **Horarios:** pedidos habilitados solo en horario de atención, considerando los feriados de Chile.

## Decisiones técnicas
- Los precios se **recalculan en el servidor**; nunca se confía en el total enviado por el navegador.
- Los secretos (Transbank, Supabase service role, claves push) están solo en el panel de Cloudflare, nunca en el repositorio.
- Las rutas de cocina y admin están protegidas con login del personal (Supabase Auth).
- Pruebas unitarias (`node --test`) y E2E con Playwright, incluyendo pruebas visuales.

## Stack
Next.js 16 (App Router) · Cloudflare Workers (OpenNext) · Supabase (Postgres, Auth, Realtime) · Transbank Webpay Plus · Tailwind CSS · Leaflet · Playwright
