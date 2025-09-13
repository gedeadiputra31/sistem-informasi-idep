## About IDEP-Training

Fitur utama dari Sistem Informasi IDEP meliputi:

### 1. **Manajemen Data Pelatihan**

- Mengelola informasi tentang berbagai program pelatihan yang ditawarkan.
- Menyimpan rincian peserta, jadwal, dan lokasi pelatihan.

### 2. **Pemantauan Kemajuan Peserta**

- Memungkinkan pemantauan kemajuan peserta selama pelatihan.
- Menyediakan laporan tentang kehadiran dan pencapaian peserta.

### 3. **Laporan Kegiatan**

- Menghasilkan laporan berkala mengenai kegiatan pelatihan.
- Menyediakan analisis dan statistik untuk evaluasi program.

### 4. **Antarmuka Pengguna yang Ramah**

- Menggunakan antarmuka berbasis AdminLTE yang intuitif dan responsif.
- Memudahkan pengguna dalam navigasi dan akses informasi.

### 5. **Keamanan Data**

- Mengimplementasikan sistem autentikasi untuk melindungi data pengguna.
- Menjamin bahwa hanya pengguna yang berwenang yang dapat mengakses informasi sensitif.

### 6. **Integrasi dengan Sistem Lain**

- Kemampuan untuk terintegrasi dengan aplikasi atau sistem lain untuk memperluas fungsionalitas.

Fitur-fitur ini dirancang untuk mendukung organisasi nirlaba dalam meningkatkan efisiensi dan efektivitas program pelatihan mereka.

### Premium Partners

- **[Siva](https://www.instagram.com/agus.maharta/)**
- **[Panca Dharma](https://www.instagram.com/panca_dharma/)**
- **[Wirawan Wira](https://www.instagram.com/wirawan.wira/)**
- **[Gede Adi Surya](https://www.instagram.com/gedeadisurya)**

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

- duplicate the code, cd into project
- open terminal, run composer install
- run php artisan key:generate
- run php artisan:migrate to run migration and make database, make sure you update .env based on your sistem
- run php artisan db:seed to seed default data and super admin user

## Log

- cd to project & run composer install to install composer dependency

- Add LTE via https://github.com/jeroennoten/Laravel-AdminLTE/wiki/Plugins-Configuration
- Install plugin sweetalert2 by running - php artisan adminlte:plugins install --plugin=sweetalert2
- use php artisan adminlte to see available command list

## RUN

cp .env.example .env

# Prompt untuk Laravel dan Blade

1. **Membuat Komponen Blade**:

   - "Buatkan saya komponen Blade untuk menampilkan daftar produk dengan nama, harga, dan gambar."

2. **Formulir Pengguna**:

   - "Tulis formulir pendaftaran pengguna menggunakan Blade, dengan validasi untuk nama, email, dan password."

3. **Menggunakan Route dan Controller**:

   - "Tunjukkan cara membuat route dan controller untuk menampilkan halaman detail produk di Laravel."

4. **Menggunakan Layouts**:
   - "Buatkan saya layout Blade dasar untuk aplikasi Laravel dengan header, footer, dan section utama."

# Prompt untuk JavaScript (jQuery)

1. **Manipulasi DOM**:

   - "Tuliskan kode jQuery untuk menampilkan pesan 'Data berhasil disimpan' setelah formulir disubmit."

2. **AJAX Request**:

   - "Buatkan saya contoh jQuery AJAX request untuk mengambil data pengguna dari API dan menampilkannya di tabel."

3. **Event Handling**:

   - "Tulis kode jQuery untuk menangani klik pada tombol dan mengubah teks pada elemen tertentu."

4. **Validasi Formulir**:
   - "Buatkan validasi jQuery untuk memastikan semua field pada formulir diisi sebelum disubmit."

# Tips Tambahan

- **Spesifik**: Semakin spesifik Anda dalam permintaan, semakin baik hasilnya.
- **Contoh**: Sertakan contoh data atau struktur yang Anda inginkan untuk mendapatkan hasil yang lebih relevan.
- **Iterasi**: Jika hasil pertama tidak memuaskan, coba ubah prompt Anda sedikit untuk mendapatkan hasil yang lebih baik.

# Teknologi yang Digunakan dalam Pengembangan Sistem Informasi IDEP

## 1. Framework

- **Laravel**: Framework PHP yang digunakan untuk membangun aplikasi web dengan struktur yang rapi dan kemudahan dalam pengembangan.

## 2. Basis Data

- **MySQL**: Sistem manajemen basis data relasional yang digunakan untuk menyimpan data aplikasi.

## 3. Antarmuka Pengguna

- **AdminLTE**: Template dashboard berbasis HTML yang digunakan untuk membangun antarmuka pengguna yang responsif dan menarik.

## 4. Bahasa Pemrograman

- **PHP**: Bahasa pemrograman yang digunakan dalam pengembangan backend aplikasi.

## 5. Frontend

- **HTML, CSS, dan JavaScript**: Digunakan untuk membangun tampilan dan interaktivitas di sisi klien.

## 6. Tools dan Library Tambahan

- Berbagai alat dan pustaka tambahan yang mendukung pengembangan, seperti Composer untuk manajemen dependensi.

---

# 🗄️ Memory-Efficient Database Seeder Guide

## 🚀 Quick Commands for Running Seeders with Memory Limits

### Method 1: Direct PHP Memory Limit

```bash
# Set memory limit directly when running artisan
php -d memory_limit=1G artisan db:seed --class=KelurahanSeeder

# For all seeders
php -d memory_limit=1G artisan db:seed

# With specific chunk size (if your seeder supports it)
php -d memory_limit=512M artisan db:seed --class=KelurahanSeeder
```

### Method 2: Using Custom Artisan Command

```bash
# First, create the custom command
php artisan make:command SeedWithMemoryLimit

# Then use it
php artisan db:seed-memory --class=KelurahanSeeder --memory=1G --chunk=1000
php artisan db:seed-memory --memory=512M --chunk=500
```

### Method 3: Environment Configuration

```bash
# Set in .env file
SEEDER_MEMORY_LIMIT=1G
SEEDER_CHUNK_SIZE=1000

# Then run normally
php artisan db:seed --class=KelurahanSeeder
```

## ⚙️ Configuration Files to Update

### 1. Update your .env file

Add these variables to your `.env` file:

```env
# Seeder Configuration
SEEDER_MEMORY_LIMIT=1G
SEEDER_CHUNK_SIZE=1000
DB_SEEDER_TIMEOUT=300
```

### 2. Update php.ini (Optional)

If you want system-wide changes:

```ini
memory_limit = 1G
max_execution_time = 300
```

### 3. Update Docker Configuration

Add this to your Dockerfile:

```dockerfile
# Set PHP memory limit for development
RUN echo "memory_limit=1G" >> /usr/local/etc/php/conf.d/docker-php-memlimit.ini \
    && echo "max_execution_time=300" >> /usr/local/etc/php/conf.d/docker-php-timeout.ini
```

## 📊 Memory Usage Monitoring

### Monitor Memory During Seeding

```bash
# Run seeder with verbose output
php -d memory_limit=1G artisan db:seed --class=KelurahanSeeder -v

# Monitor system resources (separate terminal)
watch -n 1 'ps aux | grep artisan'

# Check PHP memory usage
php -r "echo 'Memory Limit: ' . ini_get('memory_limit') . PHP_EOL;"
```

### Log Memory Usage in Your Seeder

```php
// Add this to your seeder
private function logMemory($context = '') {
    $current = memory_get_usage(true);
    $peak = memory_get_peak_usage(true);
    Log::info("$context - Current: " . ($current/1024/1024) . "MB, Peak: " . ($peak/1024/1024) . "MB");
}
```

## 🎯 Best Practices for Large Seeders

### 1. Chunk Size Recommendations

```php
// For Kelurahan data (assume ~83,000 records)
$chunkSize = 1000;  // Good balance of speed vs memory

// Adjust based on record size:
// - Simple records (few columns): 2000-5000
// - Complex records (many columns): 500-1000
// - Records with relationships: 100-500
```

### 2. Database Optimization

```php
// In your seeder
public function run() {
    // Disable foreign key checks (faster)
    DB::statement('SET FOREIGN_KEY_CHECKS=0');

    // Disable query logging (saves memory)
    DB::disableQueryLog();

    // Your seeding logic here
    $this->seedKelurahan();

    // Re-enable foreign key checks
    DB::statement('SET FOREIGN_KEY_CHECKS=1');
}
```

### 3. File-based Data Loading

```php
// For CSV files
private function seedFromCsv($filePath) {
    $file = new SplFileObject($filePath);
    $file->setFlags(SplFileObject::READ_CSV);

    $batch = [];
    $counter = 0;

    foreach ($file as $row) {
        if ($counter++ == 0) continue; // Skip header

        $batch[] = [
            'kode' => $row[0],
            'nama' => $row[1],
            // ...
        ];

        if (count($batch) >= 1000) {
            DB::table('kelurahan')->insert($batch);
            $batch = [];
            gc_collect_cycles();
        }
    }

    // Insert remaining
    if ($batch) DB::table('kelurahan')->insert($batch);
}
```

## 🐛 Troubleshooting Common Issues

### Memory Limit Exceeded

```bash
# Increase memory limit
php -d memory_limit=2G artisan db:seed --class=KelurahanSeeder

# Or reduce chunk size in seeder
$chunkSize = 500; // Instead of 1000
```

### Timeout Issues

```bash
# Increase execution time
php -d max_execution_time=600 -d memory_limit=1G artisan db:seed --class=KelurahanSeeder
```

### Database Connection Lost

```php
// In your seeder, reconnect if needed
if (!DB::connection()->getPdo()) {
    DB::reconnect();
}
```

### Progress Tracking

```php
use Illuminate\Console\Command;

public function run() {
    $total = count($this->getData());
    $bar = $this->command->getOutput()->createProgressBar($total);
    $bar->start();

    foreach ($chunks as $chunk) {
        // Process chunk
        DB::table('kelurahan')->insert($chunk);
        $bar->advance(count($chunk));
    }

    $bar->finish();
    $this->command->newLine();
}
```

## 📈 Performance Optimization Tips

### 1. Use Raw Queries for Better Performance

```php
// Instead of Eloquent models
// Kelurahan::create($data);

// Use raw inserts
DB::table('kelurahan')->insert($data);
```

### 2. Disable Model Events

```php
// If you must use Eloquent
Kelurahan::unguarded(function () {
    Kelurahan::withoutEvents(function () {
        // Your seeding logic
    });
});
```

### 3. Batch Processing with Progress

```bash
# Run seeder in background with nohup
nohup php -d memory_limit=1G artisan db:seed --class=KelurahanSeeder > seeder.log 2>&1 &

# Check progress
tail -f seeder.log
```

## 🔧 Example Usage Commands

```bash
# Standard seeding with memory limit
php -d memory_limit=1G artisan db:seed --class=KelurahanSeeder

# Seeding with custom memory and timeout
php -d memory_limit=2G -d max_execution_time=600 artisan db:seed

# Using the custom command (after creating it)
php artisan db:seed-memory --class=KelurahanSeeder --memory=1G --chunk=1000

# Multiple seeders with different limits
php -d memory_limit=512M artisan db:seed --class=ProvinsiSeeder
php -d memory_limit=1G artisan db:seed --class=KabupatenSeeder
php -d memory_limit=2G artisan db:seed --class=KelurahanSeeder
```

Remember: Always test with a subset of your data first to determine optimal chunk sizes and memory limits!

```php

<?php

// 1. MEMORY EFFICIENT SEEDER CLASS EXAMPLE
// File: database/seeders/KelurahanSeeder.php

namespace Database\Seeders;

use Illuminate\Database\Seeder;
use Illuminate\Support\Facades\DB;
use Illuminate\Support\Facades\Log;

class KelurahanSeeder extends Seeder
{
    private $chunkSize = 1000; // Process 1000 records at a time
    private $memoryLimit = '512M'; // Memory limit for this seeder

    public function run()
    {
        // Set memory limit for this seeder
        ini_set('memory_limit', $this->memoryLimit);

        // Log initial memory usage
        $this->logMemoryUsage('Starting seeder');

        // Disable query logging to save memory
        DB::disableQueryLog();

        // Method 1: Chunk Processing with Raw Data
        $this->seedWithChunking();

        // Method 2: Alternative - Stream processing
        // $this->seedWithStreaming();

        $this->logMemoryUsage('Seeder completed');
    }

    /**
     * Method 1: Chunk Processing - Best for most cases
     */
    private function seedWithChunking()
    {
        $kelurahanData = $this->getKelurahanData();
        $totalRecords = count($kelurahanData);
        $chunks = array_chunk($kelurahanData, $this->chunkSize);

        $this->command->info("Processing {$totalRecords} records in " . count($chunks) . " chunks");

        foreach ($chunks as $index => $chunk) {
            $this->command->info("Processing chunk " . ($index + 1) . "/" . count($chunks));

            // Use DB::insert for better performance
            DB::table('kelurahan')->insert($chunk);

            // Force garbage collection
            gc_collect_cycles();

            // Optional: Add small delay to prevent overwhelming the database
            usleep(100000); // 0.1 second

            $this->logMemoryUsage("After chunk " . ($index + 1));
        }
    }

    /**
     * Method 2: Streaming - For extremely large datasets
     */
    private function seedWithStreaming()
    {
        $filePath = database_path('data/kelurahan.csv'); // Assuming CSV file

        if (!file_exists($filePath)) {
            $this->command->error("Data file not found: {$filePath}");
            return;
        }

        $handle = fopen($filePath, 'r');
        $batch = [];
        $counter = 0;

        // Skip header row
        fgetcsv($handle);

        while (($row = fgetcsv($handle)) !== false) {
            $batch[] = [
                'kode_kelurahan' => $row[0],
                'nama_kelurahan' => $row[1],
                'kode_kecamatan' => $row[2],
                'created_at' => now(),
                'updated_at' => now(),
            ];

            $counter++;

            // Process batch when it reaches chunk size
            if (count($batch) >= $this->chunkSize) {
                DB::table('kelurahan')->insert($batch);
                $batch = []; // Clear the batch
                gc_collect_cycles(); // Force garbage collection

                $this->command->info("Processed {$counter} records");
                $this->logMemoryUsage("After {$counter} records");
            }
        }

        // Insert remaining records
        if (!empty($batch)) {
            DB::table('kelurahan')->insert($batch);
            $this->command->info("Final batch: {$counter} records processed");
        }

        fclose($handle);
    }

    /**
     * Get sample Kelurahan data - Replace with your actual data source
     */
    private function getKelurahanData()
    {
        // Option 1: Return static array (for smaller datasets)
        // return $this->getStaticKelurahanData();

        // Option 2: Read from CSV file
        return $this->readFromCsv();

        // Option 3: Read from JSON file
        // return $this->readFromJson();
    }

    private function readFromCsv()
    {
        $filePath = database_path('data/kelurahan.csv');
        $data = [];

        if (!file_exists($filePath)) {
            $this->command->warn("CSV file not found: {$filePath}. Using sample data.");
            return $this->getSampleData();
        }

        // For large files, consider using the streaming method instead
        $handle = fopen($filePath, 'r');
        fgetcsv($handle); // Skip header

        while (($row = fgetcsv($handle)) !== false) {
            $data[] = [
                'kode_kelurahan' => $row[0],
                'nama_kelurahan' => $row[1],
                'kode_kecamatan' => $row[2],
                'created_at' => now(),
                'updated_at' => now(),
            ];
        }

        fclose($handle);
        return $data;
    }

    private function getSampleData()
    {
        // Sample data for testing
        $data = [];
        for ($i = 1; $i <= 5000; $i++) {
            $data[] = [
                'kode_kelurahan' => str_pad($i, 6, '0', STR_PAD_LEFT),
                'nama_kelurahan' => "Kelurahan {$i}",
                'kode_kecamatan' => str_pad(ceil($i/50), 3, '0', STR_PAD_LEFT),
                'created_at' => now(),
                'updated_at' => now(),
            ];
        }
        return $data;
    }

    private function logMemoryUsage($context = '')
    {
        $memoryUsage = memory_get_usage(true);
        $memoryPeak = memory_get_peak_usage(true);

        $this->command->info(sprintf(
            '%s - Memory: %s / Peak: %s',
            $context,
            $this->formatBytes($memoryUsage),
            $this->formatBytes($memoryPeak)
        ));
    }

    private function formatBytes($bytes)
    {
        $units = ['B', 'KB', 'MB', 'GB'];
        $bytes = max($bytes, 0);
        $pow = floor(($bytes ? log($bytes) : 0) / log(1024));
        $pow = min($pow, count($units) - 1);

        $bytes /= pow(1024, $pow);

        return round($bytes, 2) . ' ' . $units[$pow];
    }
}

// 2. ARTISAN COMMAND WITH MEMORY LIMIT
// File: app/Console/Commands/SeedWithMemoryLimit.php

namespace App\Console\Commands;

use Illuminate\Console\Command;
use Illuminate\Support\Facades\Artisan;

class SeedWithMemoryLimit extends Command
{
    protected $signature = 'db:seed-memory {--class=} {--memory=512M} {--chunk=1000}';
    protected $description = 'Run database seeders with memory limit control';

    public function handle()
    {
        $class = $this->option('class');
        $memoryLimit = $this->option('memory');
        $chunkSize = $this->option('chunk');

        // Set memory limit
        $oldLimit = ini_get('memory_limit');
        ini_set('memory_limit', $memoryLimit);

        $this->info("Memory limit set to: {$memoryLimit} (was: {$oldLimit})");
        $this->info("Chunk size: {$chunkSize}");

        try {
            if ($class) {
                // Run specific seeder
                Artisan::call('db:seed', ['--class' => $class]);
                $this->info("Seeder {$class} completed successfully");
            } else {
                // Run all seeders
                Artisan::call('db:seed');
                $this->info("All seeders completed successfully");
            }

            $this->logFinalMemoryUsage();

        } catch (\Exception $e) {
            $this->error("Seeding failed: " . $e->getMessage());
            return 1;
        } finally {
            // Restore original memory limit
            ini_set('memory_limit', $oldLimit);
        }

        return 0;
    }

    private function logFinalMemoryUsage()
    {
        $memoryUsage = memory_get_usage(true);
        $memoryPeak = memory_get_peak_usage(true);

        $this->info("Final Memory Usage: " . $this->formatBytes($memoryUsage));
        $this->info("Peak Memory Usage: " . $this->formatBytes($memoryPeak));
    }

    private function formatBytes($bytes)
    {
        $units = ['B', 'KB', 'MB', 'GB'];
        $bytes = max($bytes, 0);
        $pow = floor(($bytes ? log($bytes) : 0) / log(1024));
        $pow = min($pow, count($units) - 1);
        $bytes /= pow(1024, $pow);
        return round($bytes, 2) . ' ' . $units[$pow];
    }
}

// 3. TRANSACTION-BASED SEEDER FOR SAFETY
// Alternative approach with transaction handling

class TransactionalKelurahanSeeder extends Seeder
{
    public function run()
    {
        ini_set('memory_limit', '1G');

        $chunkSize = 500;
        $data = $this->getKelurahanData();
        $chunks = array_chunk($data, $chunkSize);

        foreach ($chunks as $index => $chunk) {
            DB::beginTransaction();

            try {
                DB::table('kelurahan')->insert($chunk);
                DB::commit();

                $this->command->info("Chunk " . ($index + 1) . " completed");

            } catch (\Exception $e) {
                DB::rollback();
                $this->command->error("Chunk " . ($index + 1) . " failed: " . $e->getMessage());
                throw $e;
            }

            // Memory cleanup
            gc_collect_cycles();
        }
    }
}

```
